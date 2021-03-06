## Your Name:


# CIDM 3312 Lab 10 Part 1: Frontend and Bootstrap

## Task 0: Prepare Your Environment

1. Create an ASP.NET Core Project using the `dotnet new webapp` command.

## Task 1: Make a Razor Page with a Bootstrap Grid Layout

1. Create a new Razor Page (you don't need a page model yet) in your project.
2. Add an `<h1></h1>` tag with the text "Lab 10" inside.
3. Place an `<hr />` tag underneath that.
4. Build a Bootstrap Grid Layout with 2 rows. Remember the container div is already defined in _Layout.cshtml.
5. Row 1 should have 2 columns of size 4 and 8 respectively. Give each column a border with a color of your choice.
6. In the first column, just put the text "Column One".
7. Find an image online for the second column and use the `<img>` tag to link to it.
    * The image is a static file. Where should you put it so that you can link to it properly?
8. Row 2 should have 3 columns of all different sizes. What should the sizes add up to?
9. Give the columns a border and place whatever text you like in each column. 
10. Your entire page should look similar to the following:

![Image of webpage](https://i.imgur.com/yGDMTOs.png)

## Task 2: Add a Form to your Razor Page
1. In Column One, delete the text and put HTML/Bootstrap code for a form that uses the HTTP Post request. The form should look like the following:

![Image of form](https://i.imgur.com/KzfnP33.png)

## Task 3: Make the Page Model 
1.	Create a Page Model (.cshtml.cs file) for your Razor Page. Remember the basic code to place in a page model? Refer to `Index.cshtml.cs` or Lab 8.
      * Don’t forget the change the class name to match the name of your Razor Page.
      * Connect the Razor Page to the Page Model. 
2. Create an empty `OnPost()` method. This method will be called when you hit Submit on your form.

## Task 4: Add Logging and Verify HTTP Post
1.	Remember Logging in Lab 9? Add code to enable logging in your page model.
2.	Log an **information** message inside your `OnPost()` method that will print out “OnPost() Called”.
3.	Filter out all the Microsoft logs like you did in Lab 9 so that only your log message is displayed.
4.	Run your project, fill out the form, and hit submit. Verify that the log message is displayed to the console.
5.	If the message is not displayed, it’s time to debug. Otherwise, great work!

## Submit your assignment
1. Save your program and run it. At the terminal prompt, type `dotnet run`.
2. Edit `README.md` and put your name at the top.
3. Push your changes to GitHub:
    - Click the source control icon in VS Code
    - Type in a commit message
    - Click the checkbox icon to commit. (Click yes on the message box to stage your commit)
    - Click the 3 dots icon (...) for more actions and click Push.
4. Or you can push your changes to GitHub using the Terminal:
    ```
    git add -A
    git commit -m "Ready for grading"
    git push
    git status
    ```
5. Verify that your changes are on GitHub.
6. Congratulations! Your lab 10 part 1 assignment is complete. Move on to part 2 next week.


# CIDM 3312 Lab 10 Part 2: Model Binding

## Task 0: Prepare Your Environment

1. Open Lab 10 Part 1 in Visual Studio Code. Part 2 will push to the same repository, so you will build on your part 1 submission.

## Task 1: Model Binding Server-Side Part
Model binding links data in the web page (frontend or client-side) to C# variables in your model (backend or server-side). Your goal is to connect the data that the user inputs in your form to your page model.

1.	Your form has text boxes for First Name and Last Name. Create a FirstName property and a LastName property in your Page Model class (the .cshtml.cs file)
2.	Add the `[BindProperty]` decorators to your properties. It is this line of code that sets up the model binding. Your code should look like this:

```
[BindProperty]
public string FirstName {get; set;}
```
