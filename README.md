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
