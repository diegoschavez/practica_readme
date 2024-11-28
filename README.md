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
<li><a href ="#DM">Delete Member</a></li>
<li><a href ="#SFT">Search From The Tree</a></li>
<li><a href ="#IU">Family Tree Visualiation</a></li>
<li><a href ="#TV">SubTree Visualization</a></li>
<li><a href ="#IE">Import and Export</a></li>
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
<p><a href ="#MM">Back main menu</a></p>

<h2 id="DM">Delete Member</h2>
<p>This Function uses 2 methods to determine the way to delete the data on the tree, once you see the tree info you will see a new menu</p><p align="center"><img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/7.png?raw=true" alt="Delete Member">
</p>
<p align="center">The SubTree delete has the particularity that they will try first to find the Id with the main root on that tree and then delete both parents</p>

``` C++
std::cout << std::endl
                        << kRed << "1. Delete SubTree" << kReset << std::endl
                        << std::endl;
              target = GetTargetIDFromKeyBoard();
              node = root->findSubTree(target);
              if (node) {
                root->deleteSubTree(node);
                std::cout << "Subtree with root ID " << target
                          << " has been deleted" << std::endl;
              } else {
                std::cout << std::endl
                          << kRed << "Subtree not found" << kReset << std::endl;
```
<p>Using the **Recursive Function** to determine and take both sides and making them null to delete all the conection and conecting the member if there was anyone conected to that subtree </p>

``` C++
 deleteTreeRecursive(subTreeRoot->left);
  deleteTreeRecursive(subTreeRoot->right);

  // Unlink The main tree
  if (root == subTreeRoot) {
    root = nullptr;  // If the main root is remove, the tree is null
  } else {
    Node *parent = findParent(root, subTreeRoot);
    if (parent) {
      if (parent->left == subTreeRoot) {
        parent->left = nullptr;
        parent->data.mother = -1;
      }
      if (parent->right == subTreeRoot) {
        parent->right = nullptr;
        parent->data.father = -1;
```
<h3>Delete Member Only </h3>
<p>This function only deletes one member for the tree of subtree </p>
<p align="center"><img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/8.png?raw=true" alt="Delete Member"></p>
<p>This function only needs the ID to work and then make the reconection for the SubTree</p> 

```C++
std::cout << std::endl
                        << kRed << "2. Delete and replace with parent" << kReset
                        << std::endl
                        << std::endl;
              target = GetTargetIDFromKeyBoard();
              root->deleteMember(target);
              break;
```
<p><a href="#MM">Back to main menu</a></p>

<br><br>

<h2 id="SFT">Search From The Tree</h2>
</p>
<p align="center">The function has almost the same properties as the **Delete Function ** but this manage 3 parameters to find the member which those are </p>
<p align="center"><img width=200 height=200 src="https://github.com/diegoschavez/practica_readme/blob/main/PED/9.png?raw=true" alt="Family Tree Visualization"></p>
<p>Making a loop to search the value matching with the characters that the user wrote has the same search as the option of **Last Name**</p>

```C++
std::vector<Node *> subVector;

  for (auto &element : inorderVector) {
    if (element->data.first_name == targetMember.first_name) {
      subVector.push_back(element);
    }
  }

  std::sort(inorderVector.begin(), inorderVector.end());
  return subVector;
```
<p>The search by ID is different, it has an iterator to find all the data that matches with the number also has a pointer to find the exact value from the right structure and then shows the Data conected to that ID</p>

```C++
  auto it = std::find_if(
      inorderVector.begin(), inorderVector.end(),
      [&](Person &currentNode) { return currentNode.id == targetID; });

  if (it == inorderVector.end()) {
    return {};
  }

  return *it;
```

<p><a href="#MM">Back to main menu</a></p>

<br><br>

<h2 id="IU">Family Tree Visualization</h2>
<p>Space to explain the family tree visualization feature.</p>
<p align="center"> <img width=300 height=300 src="" alt="Family Tree Visualization">
</p>
<p align="center">Explain how the family tree is visualized and any interactive features (e.g., zooming, expanding branches).</p>

<p><a href="#MM">Back to main menu</a></p>

<br><br>

<h2 id="TV">SubTree Visualization</h2>
<p>Space to explain the subtree visualization feature.</p>
<p align="center">
    <!-- Add your image here -->
    <img width="500" height="300" src="image_url_here" alt="SubTree Visualization">
</p>
<p align="center">Explain how subtrees are visualized and how you can explore specific branches of the family tree.</p>

<p><a href="#MM">Back to main menu</a></p>

<br><br>

<h2 id="IE">Import and Export</h2>
<p>Space to explain how to import and export family tree data.</p>
<p align="center">
    <!-- Add your image here -->
    <img width="500" height="300" src="image_url_here" alt="Import and Export">
</p>
<p align="center">Explain the process of importing family tree data from external files and exporting the tree to various formats.</p>

<p><a href="#MM">Back to main menu</a></p>
