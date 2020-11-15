 

This tutorial is suitable for beginners. Especially those who have just started learning android programming in kotlin. Every app needs to follow certain architectural principles. Failure to adhere to this requirement results in low-quality applications. Such applications disappoint users. As a result, the number of uninstalls will be high.
### Introduction
Let's start by evaluating what android architectures existed before MVVM. The first component is Model View Presenter denoted by MVP. Though this architecture separates the business logic from the app's UI, it is not easy to implement. In the long-run, this can translate into high development costs. The second android architecture is [MVC](https://openclassrooms.com/en/courses/4661936-develop-your-first-android-application/4679186-learn-the-model-view-controller-pattern#:~:text=Most%20Android%20developers%20use%20a,apply%20to%20our%20TopQuiz%20application.). Just like MVP, it is also quite complex and not suitable for small projects. Google introduced MVVM (Model-View-ViewModel)  to resolve these challenges. By separating code into smaller chunks, MVVM simplifies the debugging process. Through this article, you'll understand MVVM architecture and implement it in an application. Furthermore, this article shows how to debug common errors resulting from this architecture. You can learn more about MVVM [here](https://developer.android.com/topic/libraries/architecture/viewmodel?gclid=Cj0KCQiA7qP9BRCLARIsABDaZzhDtIsNoyAcuVYiA3F3smhaKd4THplNIp1nDr-KGB_XWkzZxiIvrVAaAjYKEALw_wcB&gclsrc=aw.ds).

Let's dive in!



### Prerequisites
1. Android studio
2. You must be familiar with [Kotlin](https://developer.android.com/kotlin/campaign/learn?gclid=Cj0KCQiA7qP9BRCLARIsABDaZzh1wodOJn7w8kKTtWq8yNFlx9xoqzEE_cU2KkCO2Ecdyyr2frGOVjQaAlSuEALw_wcB&gclsrc=aw.ds)
3. Install [lifecycle](https://developer.android.com/jetpack/androidx/releases/lifecycle) dependencies
4. Download the start code from [here](https://github.com/WanjaMIKE/MVVMExample)

#### The goal of the tutorial
By the end of this tutorial, you will create an app that takes input and displays it on a recycler view. Below is the screenshot of the app.

### Step 1 – Launching Android Studio.
Launch Android Studio and create a new project, as shown below. Make sure that you select Kotlin as your preferred programming language. If you do not have Android Studio, you can install it from [here](https://developer.android.com/studio?gclid=Cj0KCQiA7qP9BRCLARIsABDaZzieBJWjBnokDdH6b0gQchoqudRXNohAGp_noSqALLuSlYuwA6EB5T4aAntwEALw_wcB&gclsrc=aw.ds)

![getting started](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/getting-started.png)

### Step 2 – Creating the model.
Create the app model. This is also referred to as the data class. To avoid confusion, create a package named model inside the java folder. Then, create a data class named Blog in the model package as shown below. For simplicity, the data class will only have one variable (title). There is no need to add getters and setters, Kotlin adds them to the class automatically.

![model](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/model.png)

### Step 3 – Creating the view.
The view is what the user sees on the screen. The UI, therefore, needs to be well structured to minimize confusion and dissatisfaction.

Open `activity_main.xml` file and change the layout from constraint to linear layout. Ensure that the orientation is set to vertical. This arranges UI components vertically in the Layout. For our app, the primary widgets are `Edittext`, `Button`, and a `RecyclerView`. Ensure that all these widgets have IDs since they are vital at a later stage. The layout design and code are shown in the image below. The section with a list showing items 0 to 9 is the `RecyclerView`. Whatever we type in the app will appear in that section once the user clicks the submit button.

![view](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/view.png)

### Step 4 – Creating the view.
Still, on the layout, we need to create the design of the element that will be shown in the `RecyclerView`. Therefore, create a file named `item.xml` and add the code shown in the image below. The design is simple since only one attribute from the data class is shown to the user.

![itemview](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/itemview.png)

### Step 5 – Create a RecyclerView Adapter
A `RecyclerView` adapter handles the binding of the `item.xml` layout to the `RecyclerView`. It also takes in a list of items and displays them to the user. The image below highlights the code for the `RecyclerView` adapter.

![recyclerviewadapter](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/recycleradapter.png)

### Step 6 – Creating a ViewModel
Create a package named `ViewModel`. Inside this folder, create a Kotlin class and name it `MainViewModel`. The class should extend android `ViewModel`. You might face an error if you failed to add lifecycle dependencies from Jetpack. The `MainViewModel` will have a mutable `livedata` item that holds the array list. It is vital to use `LiveData` since it notifies the UI in case of any data changes. The `MainViewModel` code is shown below.

![viewmodel](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/viewmodel.png)

### Step 7 – Create a ViewModel factory.
The purpose of a `ViewModel` factory is to instantiate the `ViewModel`. This prevents the app from crashing in case an activity is no found. The image below shows the guideline for the `MainViewModelFactory` .

![viewmodelfactory](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/viewmodelfactory.png)

### Step 8 – MainActivity (Connecting the code)
We have created the model, `ViewModel`, `ViewModelfactory`, and `RecyclerView`. These components need to be instantiated in this class for the application to work.

Start by declaring the `RecyclerView` and instantiating it. Make sure the layout manager for the `RecyclerView` is set as `LinearLayoutManager`.

![mainactivity](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/mainactivity.png)

### Step 9 – Results
If there are no errors in your code, it should compile and show the UI in the image below. Whatever you type in the `EditText` field should display in the `recyclerview` once the users clicks the submit button.

![results](/engineering-education/implementing-mvvm-architecture-in-android-using-kotlin/result.png)

## Conclusion
MVVM architecture has made it easy to build complex applications. As shown, it's easier to identify bugs due to the separation of business logic from the UI code. The architecture also prevents data loss, especially when the orientation of the screen changes. Ensure that all dependencies are installed before using MVVM. The measure helps prevent runtime errors.

## References
[JetPack](https://developer.android.com/jetpack/guide)

