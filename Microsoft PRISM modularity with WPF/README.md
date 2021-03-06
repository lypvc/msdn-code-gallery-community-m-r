# Microsoft PRISM modularity with WPF
## Requires
- Visual Studio 2012
## License
- Apache License, Version 2.0
## Technologies
- WPF
- ViewModel pattern (MVVM)
- XAML
- MEF
- Prism
- Dependancy Injection Pattern
## Topics
- WPF
- ViewModel pattern (MVVM)
- WPF Data Binding
- Dependancy Injection
- Modularity
## Updated
- 07/03/2013
## Description

<p>PRISM framework is specially target &nbsp;for large scale application (But you can use this for small scale application too. But complexity is high).You can use prism framework &nbsp;with WPF, Silverlight, Windows Phone and also with Windows store app (You
 have to use PRISM for windows run time ).</p>
<p>&nbsp;</p>
<p><strong><span style="font-size:large">Main &nbsp;4 Features of Prism.</span></strong></p>
<p><strong>&nbsp; &nbsp; 1. Modularity</strong>&nbsp;: You can developed the application as modules using class libarary and get all of them &nbsp; &nbsp; &nbsp;togther during the run time.</p>
<p><strong>&nbsp; &nbsp; 2. Region :&nbsp;</strong>This concept is similar to the ASP.NET master pages. Here you can define place holders and you can dynamically load view into these regions(place holders).</p>
<p><strong>&nbsp; &nbsp; 3. Command :</strong>&nbsp;Prism command are implement using ICommand interface. Prims has inbuilt command called DelegateCommand. You can implement this DelegateCommand in you view -model and then You can bind the command with view
 (Nomarly with button).</p>
<p><strong>&nbsp; &nbsp; 4. Event :&nbsp;</strong>To communicate between loosely couple&nbsp;component&nbsp;we can use event. You can use PRISM&nbsp;EventAggregator to these type of communication.</p>
<p>&nbsp;</p>
<p><span style="font-size:large"><strong>Why you should use PRISM ?</strong></span></p>
<p>Just imagine that you want to develop application which is targeting HR handing,Financial handling ,etc. Without using framework like PRISM you can develop this application.No issue. But if you want to develop this application as &nbsp;</p>
<p>&nbsp;1. Separate modules.</p>
<p>&nbsp;2. Module should be loosely couple with each other.</p>
<p>&nbsp;3. Support for testability.</p>
<p>&nbsp;4. Support for maintainability.</p>
<p>&nbsp;5. Support for extendibility.</p>
<p>Then you should use framework like PRISM.Because that's what prism framework designed and developed for by Microsoft.</p>
<p>&nbsp;</p>
<p>Before Jump into the development I assume that you have fair knowledge of following technologies.</p>
<p>&nbsp;</p>
<p>1. &nbsp;WPF</p>
<p>2. &nbsp;MVVM design pattern</p>
<p>3. &nbsp;Dependency injection design pattern.</p>
<p>&nbsp;</p>
<p>Also you need to&nbsp;<a href="http://www.microsoft.com/en-sg/download/details.aspx?id=28950">download &nbsp;</a>the Latest version of prism framework from Microsoft. After download you can extract libraries into a separate folder.</p>
<p>&nbsp;</p>
<p>Our Example</p>
<p><strong>Business Scenario :</strong></p>
<p>Lets imagine our application has two main function.</p>
<p>&nbsp; 1. Display employee information</p>
<p>&nbsp; 2. Display product information</p>
<p>&nbsp;</p>
<p>To demonstrate the PRISM capabilities I'm going to implement these two function in two different modules.Also For Implement the business logic I will implement the another module called repository module.</p>
<p>&nbsp;</p>
<p>So Let's start the development now.</p>
<p>&nbsp;</p>
<p>1. First Open the VS2012 and create new WPF project and name it as PrimsModulityWithWPF.</p>
<p>2. Delete the MainPage.xaml file from the project.</p>
<p>3. Add following references from Prism desktop folder (...\PRISM4.1\Bin\Desktop).</p>
<p>&nbsp;</p>
<ul>
<li>Microsoft.Practices.Prism.dll </li><li>Microsoft.Practices.Prism.MefExtensions.dll </li><li>Microsoft.Practices.ServiceLocation.dll </li><li>Microsoft.Practices.Prism.Interactivity.dll </li></ul>
<div>
<p>4. Also add new reference called System.CompenentModel.Composition.dll from &nbsp;Framework Assemblies.</p>
</div>
<p class="separator"><a href="http://4.bp.blogspot.com/-Wd7aTG5nauM/Uc662oL964I/AAAAAAAAAhY/GWsFzvL3n7k/s795/1..JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F4.bp.blogspot.com%2F-Wd7aTG5nauM%2FUc662oL964I%2FAAAAAAAAAhY%2FGWsFzvL3n7k%2Fs640%2F1..JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="443"></a></p>
<div>
<p>&nbsp;</p>
</div>
<div>
<p>&nbsp;</p>
</div>
<div>
<p>5. Now add new WPF Widdow to the project named as Shell.</p>
</div>
<div>
<p>6. Now your new project structure will be as bellow.</p>
</div>
<div>
<p>&nbsp;</p>
</div>
<p class="separator"><a href="http://1.bp.blogspot.com/-tEdqz1uAIGI/Uc696Eyh1-I/AAAAAAAAAho/5QBCB04uHIw/s578/2.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F1.bp.blogspot.com%2F-tEdqz1uAIGI%2FUc696Eyh1-I%2FAAAAAAAAAho%2F5QBCB04uHIw%2Fs400%2F2.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="202" height="400"></a></p>
<div>
<p>&nbsp;</p>
</div>
<div>
<p>&nbsp;</p>
</div>
<div>
<p>6. Now add new C# class and named it as&nbsp;Bootstrapper</p>
</div>
<div>
<p>7.Add new two class Libraries to your project and named them as EmployeeModule and .ProductModule and delete Class1.cs file from both project.</p>
</div>
<div>
<p>8.For both newly added class libraries add the following references.</p>
</div>
<div></div>
<p>&nbsp;</p>
<ul>
<li>Microsoft.Practices.Prism.dll &nbsp;(&nbsp;&nbsp;from Prism desktop folder) </li><li>Microsoft.Practices.Prism.MefExtensions.dll&nbsp;(&nbsp;&nbsp;from Prism desktop folder)
</li><li>Microsoft.Practices.ServiceLocation.dll&nbsp;(&nbsp;&nbsp;from Prism desktop folder)
</li><li>Microsoft.Practices.Prism.Interactivity.dll&nbsp;(&nbsp;&nbsp;from Prism desktop folder)
</li><li>System.CompenentModel.Composition.dll (From&nbsp;Framework Assemblies.) </li><li>System.Xaml&nbsp;(From&nbsp;Framework Assemblies.) </li></ul>
<div>
<p>9. Add another class Library to the solution and named it as Repository.Add the Following above references to it except the <a class="libraryLink" href="http://msdn.microsoft.com/en-US/library/System.Xaml.aspx" target="_blank" title="Auto generated link to System.Xaml">System.Xaml</a> .</p>
</div>
<div>
<p>10. Add new class called EmployeeModule.cs to EmployeeModule and implement this class as below.</p>
</div>
<p class="separator"><a href="http://2.bp.blogspot.com/-tFE3HKSfAMI/Uc7EVevKxoI/AAAAAAAAAh4/3EgKwVRV9XA/s584/3.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-tFE3HKSfAMI%2FUc7EVevKxoI%2FAAAAAAAAAh4%2F3EgKwVRV9XA%2Fs640%2F3.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="320"></a></p>
<p>To import module to our main application we need to create our module exportable. So we need to implement our module class as above. Module as should implement using IModule interface which has only one method called Initialize. This method used the Initialize
 your module before the loading. For example you can specify the view &nbsp;to navigate during the initial loading of your module. We will discuss more about this soon.</p>
<p>&nbsp;</p>
<p>Using ModuleExport attribute ([ModuleExport(typeof(ProductModule))]) We make this module as exportable.</p>
<p>&nbsp;</p>
<p>11.Now we want to implement the module class for EmployeeModule and Repository module.First write click on&nbsp;EmployeeModule and add new class called&nbsp;EmployeeModule.cs and implement it as below.</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-4QlgtkG4OQk/Uc7H6u2GwjI/AAAAAAAAAiI/kRd_jKrwWMc/s494/4.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-4QlgtkG4OQk%2FUc7H6u2GwjI%2FAAAAAAAAAiI%2FkRd_jKrwWMc%2Fs640%2F4.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="286"></a></p>
<p>&nbsp;</p>
<p>Now right click on Repository class library and add new class called RepositoryModule and Implement it as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-QxF8PtmHPZ8/Uc7JVE9vBYI/AAAAAAAAAiY/PVbPp4AfXeU/s536/5.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-QxF8PtmHPZ8%2FUc7JVE9vBYI%2FAAAAAAAAAiY%2FPVbPp4AfXeU%2Fs640%2F5.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="272"></a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>12. Now again we will move to out main project (PrimsModulityWithWPF) and we will implement the our&nbsp;Bootstrapper class and Shell.</p>
<p>&nbsp;</p>
<p><strong>Responsibility of Boostrapper :&nbsp;</strong></p>
<p>&nbsp;</p>
<p>A Bootstrapper is the one who has&nbsp;responsibility&nbsp;to initialization of your application which is&nbsp;implemented&nbsp;using prism&nbsp;library.</p>
<p>Also you want to need that PRISM provide two dependency container libraries called MEF and Unity. For MEF container PRISM has already implemented Bootstrapper class called MefBootstrapper. Also for Unity container PRISM as already implemented bootstrapper
 class called UnityBootstrapper.</p>
<p>&nbsp;</p>
<p>In our example we use dependency injection container as MEF. So we need to implement &nbsp;our boostrapper class derive from MefBootstrapper.</p>
<p>&nbsp;</p>
<p>Before jump into bootstrapper implementation &nbsp;right click on References of&nbsp;PrimsModulityWithWPF project and add the&nbsp;EmployeeModule,ProductModule and Repository as solution references.</p>
<p class="separator"><a href="http://1.bp.blogspot.com/-CBD2tYAn_1U/Uc7PcPswomI/AAAAAAAAAio/MxNa7RyASQM/s801/6.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F1.bp.blogspot.com%2F-CBD2tYAn_1U%2FUc7PcPswomI%2FAAAAAAAAAio%2FMxNa7RyASQM%2Fs640%2F6.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="440"></a></p>
<p>&nbsp;</p>
<p>Now implement our Boostrapper class as below.</p>
<p class="separator"><a href="http://4.bp.blogspot.com/-mcJ0e0zDmJ8/Uc7ldMgru0I/AAAAAAAAAi4/DI0FCy3AqjM/s1021/7.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F4.bp.blogspot.com%2F-mcJ0e0zDmJ8%2FUc7ldMgru0I%2FAAAAAAAAAi4%2FDI0FCy3AqjM%2Fs1600%2F7.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>Here we have to override some of virtual methods in which are in MefBootstrapper class</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<ul>
<li>CreateShell </li></ul>
<div>
<p>The CreateShell method allows a developer to specify the top-level Window for Prism application.Shell is usually the MainWindow of your application. (<span style="font-size:x-small">Ref : PRISM 4.1 Documentation</span>)</p>
</div>
<ul>
<li>InitializeShell </li></ul>
<div>
<p>After you create a shell, you may need to run initialization steps to ensure that the shell is ready to be displayed. Depending on whether you are writing a WPF or Silverlight application, the&nbsp;<strong>InitializeShell</strong>&nbsp;method implementations
 will vary.</p>
<p>For WPF applications, you will create the shell application object and set it as the application's main window, as shown here (from the Modularity QuickStarts for WPF).</p>
<pre>protected override void InitializeShell()
{
    Application.Current.MainWindow = Shell;
    Application.Current.MainWindow.Show();
}</pre>
<pre> (Ref : PRISM 4.1 Documentation)</pre>
</div>
<ul>
<li>ConfigureAggregateCatalog </li></ul>
<div>
<p>This method allows you to add type registration to the AggregateCatalog imperatively.For example, the our Bootstrapper registers the current assembly,EmployeeModule,ProductModule and Repository. In other word we should register the all the module that we
 use in our application inside this method.Without registering we can not use these libraries inside our application. Also you can register the Module using App.config file if you are using WPF.</p>
</div>
<div>
<p>&nbsp;</p>
<p>13. We have completed implementation of our Bootstrapper class now. So now we will implement our shell view as bellow.</p>
<p class="separator">&nbsp;</p>
<p>&nbsp;</p>
<p class="separator">&nbsp;</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-nv29Bh5YkJ0/Uc-tbpIiZaI/AAAAAAAAAjY/SW0iEQu66uI/s802/8.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-nv29Bh5YkJ0%2FUc-tbpIiZaI%2FAAAAAAAAAjY%2FSW0iEQu66uI%2Fs802%2F8.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="280"></a></p>
<p>&nbsp;</p>
<p>Also we need to create this shell view as exportable. To do that go to Shell.xaml.cs file and add the [Export] attribute as bellow.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://4.bp.blogspot.com/-CSv_efc4Kvo/Uc-uRBvnPaI/AAAAAAAAAjk/SlYApSR8AdE/s376/9.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F4.bp.blogspot.com%2F-CSv_efc4Kvo%2FUc-uRBvnPaI%2FAAAAAAAAAjk%2FSlYApSR8AdE%2Fs376%2F9.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="402"></a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>14. Now we can &nbsp;run and test our application working as expected or not. Before that we need to perform two extra steps more. For all the modules (Except our main module) , Properties of prism libraries &quot;Copy Local&quot; attribute should be set as &quot;False&quot;.
 Other wise our application throw an assembly conflict exception.</p>
<p>&nbsp;</p>
<p>Right click on &nbsp;<a class="libraryLink" href="http://msdn.microsoft.com/en-US/library/Microsoft.Practices.Prism.aspx" target="_blank" title="Auto generated link to Microsoft.Practices.Prism">Microsoft.Practices.Prism</a> which is in EmployeeModule class library and select the Properties &nbsp;and set &quot;Copy Local&quot; attribute as false.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-Xn3rwkAcs8g/Uc-wWvEIC4I/AAAAAAAAAj0/0g4KecsT5q0/s339/10.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-Xn3rwkAcs8g%2FUc-wWvEIC4I%2FAAAAAAAAAj0%2F0g4KecsT5q0%2Fs339%2F10.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="357" height="400"></a></p>
<p>&nbsp;Follow these step for all other Prism libraries (<a class="libraryLink" href="http://msdn.microsoft.com/en-US/library/Microsoft.Practices.Prism.MefExtensions.aspx" target="_blank" title="Auto generated link to Microsoft.Practices.Prism.MefExtensions">Microsoft.Practices.Prism.MefExtensions</a>, <a class="libraryLink" href="http://msdn.microsoft.com/en-US/library/Microsoft.Practices.ServiceLocation.aspx" target="_blank" title="Auto generated link to Microsoft.Practices.ServiceLocation">Microsoft.Practices.ServiceLocation</a>,<a class="libraryLink" href="http://msdn.microsoft.com/en-US/library/Microsoft.Practices.Prism.Interactivity.aspx" target="_blank" title="Auto generated link to Microsoft.Practices.Prism.Interactivity">Microsoft.Practices.Prism.Interactivity</a>). And do the same steps for all other class libraries (EmployeeModule,Repository).</p>
<p>&nbsp;</p>
<p>Now open you App.xaml file and delete StartupUri part from it. After that your App.xaml file should be like this.</p>
<p>&nbsp;</p>
<p>Now go to the App.xaml.cs class and override OnStartup method as bellow.</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-d77d4pOW6MQ/Uc-yszHlk8I/AAAAAAAAAkE/bDj8oLrmimU/s553/11.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-d77d4pOW6MQ%2FUc-yszHlk8I%2FAAAAAAAAAkE%2FbDj8oLrmimU%2Fs553%2F11.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="283"></a></p>
<p>&nbsp;</p>
<p>Now rebuild your application and run it. if you complete above steps correctly you can see the empty shell like below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-dVsw3yszsGY/Uc-0WRKUejI/AAAAAAAAAkU/WqMDiMw0yxc/s624/12.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-dVsw3yszsGY%2FUc-0WRKUejI%2FAAAAAAAAAkU%2FWqMDiMw0yxc%2Fs624%2F12.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="400" height="217"></a></p>
<p>&nbsp;</p>
<p>15. we can implement our modules one by one. First we will implement the out Repository module which contain the all the business logic.</p>
<p>&nbsp;</p>
<p>First we will implement the our model class for Employee and Product. Right click on &nbsp;Repository module and create new folder called Model.</p>
<p>&nbsp;</p>
<p>Create new class called &quot;Employee&quot; and implement it as bellow.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-1s0K8630MRw/Uc-5GaaBONI/AAAAAAAAAkk/JrTul3o1FZ0/s371/13.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-1s0K8630MRw%2FUc-5GaaBONI%2FAAAAAAAAAkk%2FJrTul3o1FZ0%2Fs371%2F13.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="400" height="221"></a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>Create new class called &quot;Product&quot; and implement it as bellow.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-fa-1wz0PVJI/Uc-5MBW3djI/AAAAAAAAAks/08BnKbPuK6M/s430/14.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-fa-1wz0PVJI%2FUc-5MBW3djI%2FAAAAAAAAAks%2F08BnKbPuK6M%2Fs430%2F14.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="400" height="173"></a></p>
<p>&nbsp;</p>
<p>Now we will implement the Interfaces for EmployeeRepository class and ProductRepository class. Right click on Repository module and create new folder called Repository and then right click on Repository folder and create new folder called Interfaces. Now
 create two interfaces named by IEmployeeRepository and IProducRepository and implement interface method definition as bellow.</p>
<p>&nbsp;</p>
<p>IEmployeeRepository</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://4.bp.blogspot.com/-N-FIw2mvfnQ/Uc-7ay8i1SI/AAAAAAAAAk8/2HhdqlGD93o/s383/15.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F4.bp.blogspot.com%2F-N-FIw2mvfnQ%2FUc-7ay8i1SI%2FAAAAAAAAAk8%2F2HhdqlGD93o%2Fs383%2F15.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="400" height="176"></a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>IProductRepository</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-dpSujHXbKAo/Uc-7gDDIG7I/AAAAAAAAAlE/1g3Z4ShgL4o/s392/16.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-dpSujHXbKAo%2FUc-7gDDIG7I%2FAAAAAAAAAlE%2F1g3Z4ShgL4o%2Fs392%2F16.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="400" height="178"></a></p>
<p>&nbsp;</p>
<p>Now right click on the Repository folder and create new class called EmployeeRepository and implement the class using IEmployeeRepository interface as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://1.bp.blogspot.com/-qYm8itXyrio/Uc_DbpSUa7I/AAAAAAAAAlU/nfpjfJVOpV0/s817/17.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F1.bp.blogspot.com%2F-qYm8itXyrio%2FUc_DbpSUa7I%2FAAAAAAAAAlU%2FnfpjfJVOpV0%2Fs817%2F17.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="316"></a></p>
<p>&nbsp;</p>
<p>Here you can &nbsp;see [Export] attribute and it enable the Exportability of the EmployeeRepository (Since we use type as IEmployeeRepository &nbsp;interface and since our class derived from same interface it enable exportability for EmployeeRepository class).</p>
<p>&nbsp;</p>
<p>Now again right click on the Repository folder and create new class call ProductRepository and implement the class definition as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://1.bp.blogspot.com/-BBZnlK6FvDI/Uc_GlP5AmhI/AAAAAAAAAlk/QZNyDZqjAj4/s803/18.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F1.bp.blogspot.com%2F-BBZnlK6FvDI%2FUc_GlP5AmhI%2FAAAAAAAAAlk%2FQZNyDZqjAj4%2Fs803%2F18.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="328"></a></p>
<p>&nbsp;</p>
<p>Our repository module implementation has completed now.</p>
<p>&nbsp;</p>
<p>16. Now we will implement out EmployeeModule. Here what we going to do is, we call the GetAllEMployee methods which is in Repository module &nbsp;and get the employee list and we will display the employee list in Shell's &quot;EmployeeRegion&quot;</p>
<p>&nbsp;</p>
<p>Also I assume that &nbsp;you have experience with MVVM design pattern and also XAML data binding.</p>
<p>&nbsp;</p>
<p>First select the EmployeeModule class library.Right click on References and add Repository project as solution reference.</p>
<p>&nbsp;</p>
<p>After that create two folders called View and ViewModel inside EmployeeModule class library.</p>
<p>&nbsp;</p>
<p>Right click on the ViewModel class and create new class called EmployeeViewModel and implement the class as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-UkUudClb9D0/Uc_6MIciW6I/AAAAAAAAAmE/abc9lsC8KGE/s653/19.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-UkUudClb9D0%2FUc_6MIciW6I%2FAAAAAAAAAmE%2Fabc9lsC8KGE%2Fs653%2F19.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p class="separator">&nbsp;</p>
<p>&nbsp;</p>
<p>You can see that EmployeeViewModel exportable because of [Export] attribute. Also look at the constructor and there we have use the [ImportingConstructor] attribute.By using this we can import the parameters to the constructor. Here we import the IEmployeeRepository
 interface here. (If you look at the EmployeeRepository class you can see that it is Exportable. So we can import it from our EmployeeViewModel constructor.). Also You can see that in constructor we used dependency injection here.It helps us to build loosely
 couple testable application.</p>
<p>&nbsp;</p>
<p>Now right click on View folder and create new WPF usercontrol. Implement the view as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://4.bp.blogspot.com/-uXQylwohhyE/Uc_6R4rDU1I/AAAAAAAAAmM/k6_4zkRHH_8/s937/20.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F4.bp.blogspot.com%2F-uXQylwohhyE%2FUc_6R4rDU1I%2FAAAAAAAAAmM%2Fk6_4zkRHH_8%2Fs937%2F20.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>Now open the EmployeeView.xmal.cs &nbsp;and implement the class as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-3OQn3jNgTa4/Uc_6_qQBDvI/AAAAAAAAAmU/QYdj9xv5pfM/s572/21.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-3OQn3jNgTa4%2FUc_6_qQBDvI%2FAAAAAAAAAmU%2FQYdj9xv5pfM%2Fs572%2F21.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>&nbsp;Now open the EmployeeModule class and &nbsp;add extra line of code as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://1.bp.blogspot.com/-9qJ9Q8vn0KQ/UdAA7uQKgsI/AAAAAAAAAm0/1Aot2ZoRcRQ/s539/22.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F1.bp.blogspot.com%2F-9qJ9Q8vn0KQ%2FUdAA7uQKgsI%2FAAAAAAAAAm0%2F1Aot2ZoRcRQ%2Fs539%2F22.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p class="separator">&nbsp;</p>
<p>&nbsp;</p>
<p>Here we import the IRegionManager iterface using [Import] attribute and we use the import object to Navigation. (or View loading).</p>
<p>&nbsp;</p>
<p>When EmployeeModule loading it first call the Initialize method. Inside method we &nbsp;load our ProductView into ProductRegion which is in Shell. For that we call the RequestNavigate method.</p>
<p>&nbsp;</p>
<p>17. Now we will implement our ProductModule.. First select the ProductModule class library.Right click on References and add Repository project as solution reference.</p>
<p>&nbsp;</p>
<p>Then create two folder called View and ViewModel on ProductModule class library.</p>
<p>&nbsp;</p>
<p>Right click on the ViewModel folder and create new class called ProductViewModel. Implement the class as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-LXNdICrAQQI/UdACcdRpjwI/AAAAAAAAAnE/cLwxs8Y_Zsw/s685/23.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-LXNdICrAQQI%2FUdACcdRpjwI%2FAAAAAAAAAnE%2FcLwxs8Y_Zsw%2Fs685%2F23.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>Now right click on the View folder and create new WPF usercontrol called ProductView. Implement it as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://1.bp.blogspot.com/-vfAMoFHHAQ0/UdADAbbRNlI/AAAAAAAAAnM/sRJRgMowBI4/s925/24.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F1.bp.blogspot.com%2F-vfAMoFHHAQ0%2FUdADAbbRNlI%2FAAAAAAAAAnM%2FsRJRgMowBI4%2Fs925%2F24.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>Now go to ProductView.xmal.cs and modified the class as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://2.bp.blogspot.com/-Ly_g8CyK4vI/UdADXa1oikI/AAAAAAAAAnU/ofahTz1ZPlk/s492/25.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-Ly_g8CyK4vI%2FUdADXa1oikI%2FAAAAAAAAAnU%2FofahTz1ZPlk%2Fs492%2F25.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>Now open the ProductModule.cs and modified the class as below.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-Rp_xva_1gXk/UdAEMVGic3I/AAAAAAAAAnc/vyowPKbjqXw/s531/26.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-Rp_xva_1gXk%2FUdAEMVGic3I%2FAAAAAAAAAnc%2FvyowPKbjqXw%2Fs531%2F26.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt=""></a></p>
<p>&nbsp;</p>
<p>Now we have completed our development.So rebuilt and run your application. If you are following steps correctly you will see the following window.</p>
<p>&nbsp;</p>
<p class="separator"><a href="http://3.bp.blogspot.com/-zcDK0iM-VXU/UdAE4eiZ_iI/AAAAAAAAAnk/ykKBEh2xs9s/s1365/27.JPG"><img src="https://images-blogger-opensocial.googleusercontent.com/gadgets/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-zcDK0iM-VXU%2FUdAE4eiZ_iI%2FAAAAAAAAAnk%2FykKBEh2xs9s%2Fs1365%2F27.JPG&container=blogger&gadget=a&rewriteMime=image%2F*" border="0" alt="" width="640" height="339"></a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>Happy Coding!!!!!!!!!!!!!!!!!!</p>
</div>
