# ДАТАТОН 2022 🚀 - КОМАНДА "EXCELLENT'S"
<center><img src=img/logo.jpg width=150px height=150px></center>

## Кейс
Сбор и анализ данных о товарах с маркетплейса 🍒***Wildberries***🍒. Категория - ***Елки***🎄. 
## Задача 
Спарсить данные с сайта, провести очистку данных. Добавить признаки высота елки, кол-во покупок и др. Выявить взаимосвязь цены с высотой елки, рейтингом товара и другими признаками, визуализация выводов.
## Авторы
БОРОДКИН Александр, САМОЙЛОВ Павел, КАДИРОВ Михаил, КЕЛАСКИНА Елизавета, ЛЕОНТЬЕВА Ольга, ЕПИШКОВ Владислав.
## Описание
Это решение задачи в рамках учебной практики по сбору и анализу данных.  

📎 Отчеты в миро - https://miro.com/app/board/uXjVP4dIqYE=/?moveToWidget=3458764541734187476&cot=14

📋 **Источники данных**:  
- https://www.wildberries.ru/catalog/novyy-god/elki - каталог анализируемого товара  
- https://www.wildberries.ru/webapi/menu/main-menu-ru-ru.json - список всех каталогов wildberries 
- https://catalog.wb.ru/catalog/new_year1/catalog?appType=1&curr=rub&dest=-1075831,-7[…]0,69,1,48,22,66,31,40&sort=popular&spp=0&subject=260;7295;3738 - информация о товарах из пользовательской категории постранично  
- https://www.wildberries.ru/catalog/17371819/detail.aspx?targetUrl=GP - карточка товара по определенному артикулу (в примере артикул 17371819)

💼 **Структура датасета**  
Набор данных о товаре елка с маркетплейса Wildberries, включающий в себя:
- Цена, Цена со скидкой, Скидка
- Бренд
- Кол-во отзывов (feedbacks) и рейтинг товара (rating)
- Количество раз купили	
- Подсветка
- Страна производства
- Высота упаковки, Длина упаковки, Ширина упаковки
- Высота елки, Категория высоты елки
- Вес с упаковкой (кг)

📈 **Описание результата** 
- ***Сбор и очистка данных***  
Датасет сформирован из данных о товарах из пользовательской категории елки и объединенных данных из карточек товаров с выделенными признаками (доп информация в карточках товаров и кол-во покупок). Первоначально получили *9207* строк, после парсинга карточек товаров (были удаленные страницы в процессе нашей работы), удаления строк с сопутствующими товарами таких как, подставки, юбки, венки и т.д., удаления дубликатов, в итоге осталось **6221** строка. Проведена очистка по признакам, в т.ч. удаление колонок с пропусками более 30%, заполнение пропусков в оставшихся колонках, заполнение высоты елки (данные были записаны в м, мм, см, содержали лишние символы и значения, при отсутствии данных подтягивали их из колонки Наименование). Подробнее об очистке данных в ноутбуке [Очистка_первый_этап.ipynb](https://github.com/calabarOlga/dataton_christmas_tree/blob/main/notebooks/%D0%9E%D1%87%D0%B8%D1%81%D1%82%D0%BA%D0%B0_%D0%BF%D0%B5%D1%80%D0%B2%D1%8B%D0%B9_%D1%8D%D1%82%D0%B0%D0%BF.ipynb) и файле [ИТОГОВЫЙ ОТЧЕТ]().
- 
кластеризация, выделены дополнительные признаки, проведен общий разведочный анализ данных, по категориям  
Выводы  
Графики  
Выявлено влияние на целевой признак цена со следующими признаками: высота елки, рейтинг товара, кол-во покупок?.  
Вывод Цена-Высота елки  
График  
Вывод Цена-Рейтинг товара  
График  
Вывод Цена-Кол-во покупок  
График  

## Структура репозитория
📁 **Каталог *data*** содержит данные, полученные путем парсинга.  
> 📑 *Елки_from_0_to_10000000.xlsx* - данные о товарах с маркетплейса из пользовательской категории.  
> 📑 *ind_from_0_to_2000.xlsx* - данные из карточек товаров, первые 2000.  
> 📑 *елкиExcel.xlsx* - предобработанные данные с товарами из категории.  
> 📑 *ind_from_0_to_5000.xlsx* - данные из карточек товаров, первые 5000.  
> 📑 *ind_from_5001_to_7000.xlsx* - данные из карточек товаров, c 5001 по 7000.  
> 📑 *ind_from_7001_to_10000.xlsx* - данные из карточек товаров, c 7001 и до конца.  
> 📑 *final_data_for_cleaning_and_working_with_gaps.xlsx* - данные для очистки и анализа, сформированный из данных о товарах из пользовательской категории и объединенных данных из карточек товаров с выделенными признаками (доп информация в карточках товаров и кол-во покупок).  
> 📑 *cleaned_up_transformed_data.xlsx* - очищенные данные для формирования датасета для анализа (1 этап).  
> 📑 ***final_data_for_analysis.xlsx*** - очищенные данные (2 этап), готовый датасет для дальнейшего анализа.

📁 **Каталог *notebooks*** содержит решение в формате Jupyter Notebook.  
> 🗄️ *Парсер_Елки.ipynb* - код парсинга данных из пользовательской категории постранично, на выходе - сформированные данные в формате xlsx.  
> 🗄️ *Парсер_Елки_Страницы_Продукта.ipynb* - код парсинга данных по карточкам товара (кол-во покупок, доп информация о товаре), на выходе - сформированные данные в формате xlsx.  
> 🗄️ *Сбор_итогового_датасета_и_выделение_дополнительных_фичей.ipynb* - код сбора данных для очистки и анализа, выделения признаков из доп информации в карточках товаров и кол-во покупок, на выходе - сформированные данные в формате xlsx.  
> 🗄️ *Очистка_первый_этап.ipynb* - код очистки данных, формирования новых признаков, на выходе - сформированные данные в формате xlsx.  
> 🗄️ *---.ipynb* поверхностный анализ данных на корректность и непротиворечивость, разведывательный анализ данных (взаимосвязь между факторами, распределение классов, исследование влияния факторов на целевую переменную), визуализация данных (как распределений отдельных признаков, так и всего датасета).

📁 Каталог *project_description* содержит план работы, карточки членов команды, предварительный отчет, общие выводы по плану.

