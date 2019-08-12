# GraphCreator
Редактор графов, который поможет Вам построить граф, а так же применить алгоритм Дейкстры.

# Архитектурные решения
## Идеи 
* Архитектура данного приложения построена на основе шаблона проектирования MVC (Model View Controller). Суть данного шаблона заключается в том, что любое действие пользователя обрабатывается в контроллере, который имеет доступ к модели (Контроллер изменяет состояние модели). View отображает текущее состояние модели. Таким образом, выделив 3 интерфейса (GraphCreatorСontroller, GraphCreatorView, GraphCreatorModel) разрабатывать данное приложение можно независимо в трех «плоскостях».

*	Для того, чтобы пользователь мог добавлять, перемещать, соединять вершины, а так же удалять элементы графа был применен шаблон проектирования State (Состояние). Пользователь имеет 2 рычага управления – нажать и отпустить кнопку мыши. В разные моменты времени эти два рычага выполняют разные действия: добавить вершину, удалить элемент графа и так далее. Чтобы не писать большие условные конструкции был применен шаблон проектирования State. Были выделены следующие состояния: DeleteState, MoveState, AddVertexState, ConnectionVertexState, AlgorithmShortestWayState. Контекстом для данных состояний стал контроллер, который имеет поле currentState и обрабатывает действия кнопки мыши. Смена состояний происходит путем обработки нажатий на соответствующие кнопки.

* Следующая задача заключалась в том, чтобы разработать алгоритм таким образом, чтобы он не зависел от его отображения. Первая идея была в том, чтобы вынести реализацию  алгоритма в другой модуль и написать его так, будто выполняется консольное приложение. Вторая идея была в том, чтобы применить шаблон проектирование Adapter. Прежде чем запустить алгоритм, данные преобразовываются в необходимый формат, алгоритм выполняется, а затем данные обратно преобразовываются для отображения.

* Следующая проблема заключалась в реализации пошаговой визуализации работы алгоритма.  Решить эту задачу помогла идея шаблона проектирования Снимок. Был создан класс MementoShortestWay, который хранит в себе текущую вершину, обработанные вершины, вершины в очереди, текущие пути до вершин. В определенные моменты алгоритма в контейнер закидываются снимки текущего состояния алгоритма. Затем, когда необходимо сделать шаг вперед просто отображается i+1 снимок.

## UML
MVC | 
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/mvc.jpg" width="900" height="450">|

Adapter|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/adapter.jpg" width="900" height="450">|

State|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/state.jpg" width="900" height="500">|

# Screenshots
Start|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/1.jpg" width="900" height="450">|

Create Vertex|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/2.jpg" width="900" height="450">|

Moving Vertex|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/3.jpg" width="900" height="450">|

Create Edge|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/4.jpg" width="900" height="450">|

Saving graph|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/5.jpg" width="900" height="450">|

Loading graph|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/6.jpg" width="900" height="450">|

Big graph|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/7.jpg" width="900" height="450">|

Algorithm|
:-------------:|
<img src="https://github.com/eduard1abdulmanov123/GraphCreatorApplication/blob/master/screenshot/9.jpg" width="900" height="450">|
