# Pfolio.html
A simple portfolio system for static HTML sites.

## description:
Pfolio.html is a simple one file... or maby two file gallery/portfolio solution.
The aim is to provide static sites with a simple to understand, copy-and-paste type solution to make an immage gallery apear on their static site.

### Development and aproaches:
Pfolio.html is thus far developed solely by me, an amature hoby-dev, so im happy to merge any pull requests that improve on security, adds in some best practices, or that simply makes the code less dumb.

However, there are a few things i am quite adamant about keeping inspite of their strangeness:
1. The clumping together of JS, CSS, and HTML based on what "component" of the script they are related to

    **Reason:**    This keeps the code easier to parse when it comes to the newbie user who might just want to copy paste a part of the code for use in their site.

3. Usage of the over all system whereby the Pfolio.html file contains all of the reused styling and code to make the gallery work, the information about the location and name of the galery image files is stored in a separate file, and the setting of variables related to the function and presentation of the gallery is entered within the HTML of the page that intends to include the Pfolio.html file.

    **Reason:**    It fits my usecase! and it makes it relatively simple to have a semi-hardcoded aproach where, should you want to change the immage files and descriptions without having to edit a bunch of html, you simply have to upload the images in question and make a DirContentList.js file to match! or even better use the provided script to autogenerate those from a filder of apropriately named files! [WORK IN PROGRESS]

## Documentation:

### USAGE:
```
<script> LangNR = 0 ; </script>  
<script src="<path-to-DirContentList.js>"></script>
<script src="http://code.jquery.com/jquery-1.10.2.js"></script>
<script> $(function(){ $('.PFOLIO').load("  <path-to-Pfolio.html>  "); }); </script>
<div class="PFOLIO"></div>
```  

The snippet above should be included in the host (the HTML file that intends to use Pfolio.html).
this example uses JQuery and is, thus far, the only code at all tested.

DirContentList.js looks something like this and needs to contain the following:

```
<script>
picFiles = [“foo.png”, “bar.png”]    //names of all image files in the directory 
picDir = “/public/Portfolio/”        //path to the directory 
</script>
```

The name of the image file is used as the description, i.e., the text displayed below the image in the big-picture view. 
Image file names can contain a separator `` !NEWLANG! `` to trigger multilingual mode, where the text after `` !NEWLANG! `` is language 1 and the text before is language 0.
The name of an image file could thus be:
`` foo_-_ord_och_meningar_!NEWLANG!_foo_-_words_and_sentences.png ``   
Here, underscores are used instead of spaces! (These are replaced with spaces at runtime, so underscores cannot be used in descriptions)
If it looks like this, the code will select the language based on the variable `` LangNR `` defined in the host file (as defined above). 
You can also have more languages than that, but the code hasn’t been thoroughly tested for that purpose. 
The hyphen with spaces (underscores) on either side ``_-_`` separates the name and the description.

#### TLDR:
1. Copy the Pfolio.html file into your websites source code.
2. Make your DirContentList.js file and the folder with your imagefiles as specified above and copy these into your websites source code. An example for the contents of DirContentList.js is provided below

```
<script>
picFiles = [“foo.png”, “bar.png”]    //names of all image files in the directory 
picDir = “/public/Portfolio/”        //path to the directory 
</script>
```
   
3. Copy the following code snippet into the HTML file of the page the Pfolio image galery should appear in, replacing the <path-to-DirContentList.js> and <path-to-Pfolio.html> with the paths to the specified files as well as setting the LangNR variable to the relevant value if multiple language mode is to be used.

```
<script> LangNR = 0 ; </script>  
<script src="<path-to-DirContentList.js>"></script>
<script src="http://code.jquery.com/jquery-1.10.2.js"></script>
<script> $(function(){ $('.PFOLIO').load("  <path-to-Pfolio.html>  "); }); </script>
<div class="PFOLIO"></div>
```  

4. Edit the Css in Pfolio.html to match your desired look! [ making the css more variable driven and easily edditable is in the works ]

#### additional info:
the project has so far only been tested with .png immages and with limited special characters! that is to say only english alphanumerics as well as Å, Ä, and Ö. so please make a feature suggestion if further compatibility is needed! 

## LICENSE:

This project is published under a modified MIT license, the FlimpMIT licence, which is defined as folows for this project:

```
Copyright (c) 2026 Filippos Kokkalis

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), 
to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, 
and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. 
You are, however, allowed to not include all information as long as proper credit is given to the project this licence is applied to.
Minimal credit is defined as follows: 
Pfolio.html was made by Filippos Kokkalis and used in this project under the conditions of a modified MIT licence.
The licence and all other parts of the project can be found at [ https://github.com/Flimpflomp/Pfolio.html ]

In adition. should you (the person using this software in any capacity for your project) and I (Filippos Kokkalis) meet, 
you owe me a small symbolic gift such as a cheap snack or a trinket found on the ground.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, 
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, 
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

feel free to copy this snippet into a file in your project or in an HTML comment on your website! 
