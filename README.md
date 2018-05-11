<h3>ТЕСТОВОЕ ЗАДАНИЕ НА ПОЗИЦИЮ PYTHON РАЗРАБОТЧИКА</h3>
<h4>I. Описание части системы:</h4>
<p>Существует две системы CRM и ERP, которые имеют собственные API (REST).</br>
В CRM системе есть сущность Application (Заявка) со следующими полями:</p>

<table>
  <tr>
  <th>Название</th>
  <th>Тип</th>
  <th>Описание</th>
  </tr>
  <tr>
    <td>id</td>
    <td>int4</td> 
    <td>Первичный ключ</td>
  </tr>
  <tr>
    <td>name</td>
    <td>varchar(50)</td> 
    <td>Название заявки</td>
  </tr>
  <tr>
    <td>agreement_id</td>
    <td>int4</td>
    <td>Идентификатор договора</td>
  </tr>
  <tr>
    <td>created</td>
    <td>timestamptz</td>
    <td>Дата создания заявки</td>
  </tr>
  <tr>
    <td>updated</td>
    <td>timestamptz</td>
    <td>Дата обновления заявки</td>
  </tr>
</table>


<p>Операторы КЦ работают с сущностью Application через административный интерфейс Django.</br>
На странице просмотра объекта Application (Заявка) есть две вкладки:</p>
<ul>
  <li>Основная информация</li>
  <li>Платежи</li>
</ul>
<p>Операторам необходимо посмотреть информацию о платежах, связанных с этой заявкой.</br> 
Для этого они переходятна вкладку «Платежи». </br>
При переходе на вкладку «Платежи» выполняется HTTP запрос к ERP API для получения списка платежей,</br> 
связанных по agreement_id с текущей заявкой.</p>
<p>Пример запроса ERP API для получения платежей по id договора (agreement_id):</p>
<ol>
  <li>метод GET</li>
  <li>url: <a href="">https://host/api/v2/agreements/{:agreement_id}/payments</a></li>
  <li>headers:
    <ul>
      <li>Content-Type: application/json</li>
      <li>Access-Token: A8oMYPs8nL71obvF6zcJK0Xjo</li>
    </ul>
  </li>
</ol>
<p>В качестве авторизации ERP API проверяет на корректность заголовок &quot;Access-Token&quot;.</br>
Если значение заголовка &quot;Access-Token&quot; некорректно, то ERP API отдает HTTP статус 403.</p>
<p>Пример тела успешного ответа с платежами:
<pre>
<code>  
[
&emsp;{  
&emsp;&emsp;&quot;id&quot;:23,
&emsp;&emsp;&quot;amount&quot;:260.0,
&emsp;&emsp;&quot;date&quot;:&quot;2017-02-21&quot;
&emsp;},
&emsp;{  
&emsp;&emsp;&quot;id&quot;:53,
&emsp;&emsp;&quot;amount&quot;:1230.0,
&emsp;&emsp;&quot;date&quot;:&quot;2017-02-25&quot;
&emsp;}
&emsp;{  
&emsp;&emsp;&quot;id&quot;:23,
&emsp;&emsp;&quot;amount&quot;:260.0,
&emsp;&emsp;&quot;date&quot;:&quot;2017-02-21&quot;
&emsp;},
&emsp;&emsp;{  
&emsp;&emsp;&quot;id&quot;:53,
&emsp;&emsp;&quot;amount&quot;:1230.0,
&emsp;&emsp;&quot;date&quot;:&quot;2017-02-25&quot;
&emsp;}
]
 </code>
 </pre>
</p>
<h4>II. Задания:</h4>
<ol>
  <li>Эмулировать работу ERP API, то есть написать API, который будет возвращать список платежей </br> 
  по id договора (agreement_id). Список платежей хранится в JSON-файле.</li>
  <li>При переходе на вкладку «Платежи» выполнить запрос к ERP API и получить список платежей.</br> 
  После этого отобразить платежи на этой вкладке.</li>
</ol>

<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
