# getSortBlock

Сниппет getSortBlock идёт в комплекте с eFilter и является аналогом evoSortBlock и также используется для вывода блока сортировки и селектора количества элементов на странице.

Всё аналогично evoSortBlock, но отличаются названия параметров.

---

## Параметры

| Параметр              | Описание |
|------------------------|----------|
| `sortBy`               | По умолчанию menuindex (может быть как поле из site_content, так и любое ТВ, которое выводится в списке через DocLister и, соответветственно указано в его параметре tvList. |
| `sortOrder`            | Направление сортировки: `ASC` или `DESC`. По умолчанию: `DESC`. |
| `sortDisplay`          | Количество элементов на странице. По умолчанию: `12`. |
| `config_sort`          | Конфиг параметров сортировки (первая часть до || - заголовок, остальные - варианты. Может быть как поле site_content , так и приемлемый для DocLister TV). По умолчанию - Сортировать по:||pagetitle==Названию||price==Цене. |
| `config_display`       | Настройка селекта "показывать по". По умолчанию - Показывать по:||==--не выбрано--||10||20||30||40||all |
| `sortRow`              | Шаблон одного элемента сортировки. |
| `sortOuter`            | Обёртка для блока сортировки. |
| `displayRow`           | Шаблон одного пункта выбора количества на страницу (одна <option>). |
| `displayOuter`         | Обёртка для блока выбора количества элементов. По умолчанию содержит <select>. |
| `classActiveName`      | CSS-класс активного пункта сортировки. По умолчанию: `active`. |
| `classUpName`          | Класс сортировки по возрастанию (`ASC`). По умолчанию: `up`. |
| `classDownName`        | Класс сортировки по убыванию (`DESC`). По умолчанию: `down`. |
| `classSelectedName`    | Класс активного `<option>` в селекте. По умолчанию: `selected`. |
| `ajax`                 | Использовать AJAX. `0` — нет, `1` — да. |

---

## Пример вызова (Blade)

```blade
evo()->runSnippet('getSortBlock',[
            'sortRow'=>'<a href="#" class="sorter sort_vid sort_pic [+classActive+] [+classUpDown+]" data-sort-by="[+sortBy+]" data-sort-order="[+sortOrder+]">[+title+]</a>',// &sortRow - шаблон для вывода элемента сортировки
            'classActiveName'=>'is-active',// &classActiveName класс активного элемента
            'config_sort'=>'||pagetitle==Название||pub_date==Дата поступления||price==Цена',// &config_sort - конфиг параметров сортировки (первая часть до || - заголовок, остальные - варианты. Может быть как поле site_content , так и приемлемый для DocLister TV). По умолчанию - Сортировать по:||pagetitle==Названию||price==Цене (по названию и цене)
            'sortBy'=>'menuindex',// &sortBy - по умолчанию menuindex (может быть как поле из site_content, так и любое ТВ, которое выводится в списке через DocLister и, соответветственно указано в его параметре tvList
            'sortOrder'=>'DESC',// &sortOrder - ASC | DESC (по умолчанию DESC)
            'sortDisplay'=>'12',// &sortDisplay - Количество выводимых элементов на странице. Также берётся из сессии или из параметра $param['display'], по умолчанию — 12.
            'sortOuter'=>'<div class="eFilter_sort_block"><span class="eFilter_sort_title">[+title+]</span><span class="eFilter_sort_options">[+rows+]</span></div>',// &sortOuter - Обёртка для всех пунктов сортировки.
            'displayOuter'=>'<div class="eFilter_display_block"><span class="eFilter_display_title">[+title+]</span><span class="eFilter_display_options"><select name="sortDisplay" class="eFilter_display_select">[+rows+]</select></span></div>',//&displayOuter - Обёртка для блока выбора количества элементов. По умолчанию содержит <select>
            'displayRow'=>'<option value="[+value+]" [+selected+]>[+title+]</option>',//&displayRow - Шаблон одного пункта выбора количества на страницу (одна <option>).
            'classUpName'=>'up',//classUpName - Класс для сортировки по возрастанию (ASC). По умолчанию up.
            'classDownName'=>'down',//&classDownName - Класс для сортировки по убыванию (DESC). По умолчанию down.
            'classSelectedName'=>'selected',//&classSelectedName - Класс, добавляемый к выбранному значению в селекте. По умолчанию selected
            'config_display'=>'Показывать по:||==--не выбрано--||10||20||30||40||all==все',// &config_display - настройка селекта "показывать по". По умолчанию - Показывать по:||==--не выбрано--||10||20||30||40||all
            'ajax'=>'0'//использовать ajax. 0 - нет, 1 - да
        ]);
```
---

## Пример вызова (обычный шаблонизатор Evolution CMS 1.4)
```
[!getSortBlock?
  &sortRow=`<a href="#" class="sorter sort_vid sort_pic [+classActive+] [+classUpDown+]" data-sort-by="[+sortBy+]" data-sort-order="[+sortOrder+]">[+title+]</a>`
  &classActiveName=`is-active`
  &config_sort=`||pagetitle==Название||pub_date==Дата поступления||price==Цена`
  &sortBy=`menuindex`
  &sortOrder=`DESC`
  &sortDisplay=`12`
  &sortOuter=`<div class="eFilter_sort_block"><span class="eFilter_sort_title">[+title+]</span><span class="eFilter_sort_options">[+rows+]</span></div>`
  &displayOuter=`<div class="eFilter_display_block"><span class="eFilter_display_title">[+title+]</span><span class="eFilter_display_options"><select name="sortDisplay" class="eFilter_display_select">[+rows+]</select></span></div>`
  &displayRow=`<option value="[+value+]" [+selected+]>[+title+]</option>`
  &classUpName=`up`
  &classDownName=`down`
  &classSelectedName=`selected`
  &config_display=`Показывать по:||==--не выбрано--||10||20||30||40||all==все`
  &ajax=`0`
!]
```



