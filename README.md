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

## Task 2: Model Binding Client-Side Part
1.	Open the Razor Page (the .cshtml file). Use tag helpers to link the `<label>` and `<input>` tags to your C# properties you created in Round 1.
      * The tag helper you will use is `asp-for="PropertyName"`. PropertyName should match the exact name of the C# property  (e.g. `asp-for="FirstName"`).
2.	Delete the text between the `<label>` opening and closing tags. The `asp-for` tag helper automates writing that text.
3.	Run your project. Click view source in the web browser and see what the HTML code looks like now with the tag helpers.

## Task 3: Verify
1.	We added logging last time. Change the log message in OnPost() to print out the content of the FirstName and LastName properties.
2.	Run your project again and confirm that those properties are being set correctly.

## Task 4: Bring it Back Around
1.	Add code to your Razor Page that will display the contents of the FirstName and LastName properties back on the webpage. Remember how to display C# variables in Razor Pages?
2.	Run your project again and take a look.

## Task 5: Data Annotations
You may have noticed that the labels for your textboxes say “FirstName” and “LastName” now with no spaces. The asp-for tag helper pulls the exact variable name as the label name. Usually we don’t want that.

1.	Add the following using directives to enable Data Annotations: 
```
using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;
```
2.	Add a Data Annotation to your properties on the page model right below `[BindProperty]`:
`[Display(Name = "First Name")]`
3.	Run your project again and take a look.

## Task 6: Data Validation
Data Validation requires two parts – data annotations on the server side that specify the validation rules and tag helpers on the client side to enforce the rules.

1.	Open your razor page (.cshtml file) and add the following HTML after the `<input>` tag for each textbox. Change `"FirstName"` to match the proper variable name.
`<span asp-validation-for="FirstName" class="text-danger"></span>`
2.	Bring in the JS code to perform the validation. At the bottom of your razor page add the following:
```
@section Scripts {
    @{await Html.RenderPartialAsync("_ValidationScriptsPartial");}
}
```
3.	Add the `[Required]` and `[StringLength]` validation rules to your page model (the .cshtml.cs file). For `[StringLength]` use a max length of 60 and minimum length of 3.
4.	Run your project and test it out.

## Task 7: Data Validation Challenge - Extra Credit
Visit https://docs.microsoft.com/en-us/aspnet/core/mvc/models/validation for examples and other validation rules you can use.

1.	On your form, add an input tag (text box) for a credit card number.
2.	Review the previous rounds in this lab and write all the required code for the credit card number following the example for FirstName. 
3.	Give the credit card number the proper data validation rules. Follow the example from Round 6 but use credit card validation rules.
4.	Credit Card validation requires one more JS file imported. Open `Pages\Shared\_ValidationScriptsPartial.cshtml` and add this line:
```
<script src="~/lib/jquery-validation/dist/additional-methods.min.js"></script>
```
5.	The website at https://www.paypalobjects.com/en_AU/vhelp/paypalmanager_help/credit_card_numbers.htm 
has sample credit card numbers. Verify that your validation rules work properly.

## Submit your assignment. You are now finished with Lab 10 Part 2

