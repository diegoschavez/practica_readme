<h2><a></a></h2>
<h3><a></a></h3>
<li><a></a></li>
<p><a></a></p>
<p></p>
<img></img>
<a></a>


<h1>Family Tree</h1><p align = "centarte">The project has the objective to shows how we can connect a object that has more that one value with the purpose of manage, add, find, print and delete the relation for each object. </p>
<p align = "center"><img width="300" height="300" src="https://media.istockphoto.com/id/1392517869/es/vector/%C3%A1rbol-geneal%C3%B3gico-familiar-padres-y-abuelos-ni%C3%B1os-genealog%C3%ADa-pedigr%C3%AD-concepto-geneal%C3%B3gico.jpg?s=612x612&w=0&k=20&c=1O8pbJwhaxkXlOYx-z_JacOTEeOGcE72bepjIeofLyY="></img></p><h2 id = "MM">Main Menu</h2>
<li><a href ="#RC">Run the Code</a></li>
<li><a href ="#AM">Add Member</a></li>
<li><a href ="#IE">Import and Export</a></li>
<li><a href ="#DM">Delete Member</a></li>
<li><a href ="#IU">Input Utilities</a></li>
<li><a href ="#SFT">Search From The Tree</a></li>
<li><a href ="#TV">Tree Visualization</a></li>
<br>
<br>
<h2 id = "RC">Run the code</h2><p align ="Center">Clone the repository and paste it on your files using git bash or powershell</p><p align = "center"><img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/1.png?raw=true"</img></p>
<p align ="Center">You can use powershell to open the Folder and the code and create the file exportable file: **file.exe**</p><p align = "center"><img width="400" height="200" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/2.png?raw=true"</img></p>
<p align ="Center">Use the command **cd \name of the folder** to surf on your files and find the one who has the repository and then write the next lines to prepare the exportable file and then execute</p><p align = "center"><img width="600" height="200" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/3.png?raw=true"</img></p>
<p align ="Center">The first thing to access to the code is create the main root: First, Last name and gender the base for the tree with the ID and then you will access to the main project</p><p align = "center"><img width="350" height="350" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/4.png?raw=true"</img></p><p><a href ="#MM">Back main menu</a></p>
<br>

<h2 id = "AM">Add The Member</h2>This Function takes the data from the current user and will insert on the sub tree selected <p align = "center">
<img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/6.png?raw=true"</img></p>
<p align = "center">The Functions shows you the current tree and takes the value from the member with the **ID** to merge the two members and compare if there is already a member on the subtree (as for example mother "f" or father "m") or not in order to add the new family member</p>

``` C++
		std::cout << std::endl
                  << kGreen << "|-- 1. Insert family member" << kReset
                  << std::endl
                  << std::endl;
        root->Print2D();
        target = GetTargetIDFromKeyBoard();
        std::cout << std::endl;
        currentMember = CreateMemberFromKeyBoard();
        InsertFamilyMember(root, target, currentMember);
        root->Print2D();
```

