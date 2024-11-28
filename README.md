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

```C++
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
<p>Making a loop to search the value matching with the characters that the user wrote and has the same input as the function  **Fin by the Last Name**</p>
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
<p>The search by ID is different, it has an iterator to find all the data that matches with the number wrote it also has a pointer to find the exact value from the right structure and then shows the Data conected to that ID</p>

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
<p>The **Vector** is the main library for showing the member in a way ordered by the ID and also respecting the rule for father o mother making it as a **for function ** to travel for all the  structure and added as the last member </p>

```C++
std::sort(personCollection.begin(), personCollection.end());
  Person currentMember;
  Person mother;
  Person father;
  // Inserts root
  Tree *treeFromVector = new Tree(personCollection[0]);
  int lastMember = 0;

  for (size_t i = 0; i < personCollection.size(); ++i) {
    currentMember = personCollection[i];
    if (currentMember.father != -1) {
      father = SearchPersonByID(personCollection, currentMember.father);
      InsertFamilyMemberFromVector(treeFromVector, currentMember.id, father,
                                   currentMember.father);
    }
    if (currentMember.mother != -1) {
      mother = SearchPersonByID(personCollection, currentMember.mother);
      InsertFamilyMemberFromVector(treeFromVector, currentMember.id, mother,
                                   currentMember.mother);
    }
  }

  if (currentMember.id > lastMember) lastMember = currentMember.id;
  if (father.id > lastMember) lastMember = father.id;
  if (mother.id > lastMember) lastMember = mother.id;
  treeFromVector->setLastMember(lastMember);

  return treeFromVector;
```
<p align="center"> This one explain the mainly  way to print and use the recursive of the father and mother to be ordered and also by the right and after calling again the functio to completed the method for the left </p>

```C++

	void Tree::Print2DRecursive(Node *root, int space) const {
  if (root == nullptr) {
    return;
  }
  const int kSpace = 10;
  space += kSpace;

  Print2DRecursive(root->right, space);
  std::cout << std::endl;
  for (int i = kSpace; i < space; i++) std::cout << "   ";
  if (root->left != nullptr || root->right != nullptr)
    std::cout << root->data << " <\n";
  else
    std::cout << root->data << "\n";
  Print2DRecursive(root->left, space);
```

<p><a href="#MM">Back to main menu</a></p>

<br><br>

<h2 id="TV">SubTree Visualization</h2>
<p>On the menu is called **Print Relation Between Family Members** that is used only for check the conection as a SubTree as it is a Tree for itself having the benefit when we have plenty members on the base tree. The first step is finding the level that is the sub tree to print and then use it to travel only his relation </p>

```C++
 root->Print2D();
        root->inorderVector(inorderNodes);
        std::cout << std::endl
                  << "\x1b[32mFrom Member\x1b[0m" << std::endl
                  << std::endl;
        target = GetTargetIDFromKeyBoard();
        subTree = new Tree();
        subTree->root = SearchByID(inorderNodes, target);
        // Gets name of the target son to preserve the data
        aux_name = subTree->root->data.first_name;
        std::cout << "Member get: " << aux_name << std::endl;
        std::cout << std::endl
                  << "\x1b[32mTo Member\x1b[0m" << std::endl
                  << std::endl;
        target = GetTargetIDFromKeyBoard();
        currentLevel =
            subTree->findLevel(SearchByID(inorderNodes, target)->data);
        if (currentLevel == -1) {
          std::cout << std::endl
                    << "\x1b[31mNot Found\x1b[0m" << std::endl
                    << std::endl;
          break;
```

<p align="center">Explain how subtrees are visualized and how you can explore specific branches of the family tree and also has the function to travel for each sub level to find the one as the same as the input for the user and printed </p>

```C++
int Tree::findLevelRecursive(Node *node, const Person &value, int level) const {
  if (node == nullptr) {
    return -1;  // return -1 if there is no level
  }

  if (node->data == value) {
    return level;
  }

  // Search the member on the left side.
  int leftLevel = findLevelRecursive(node->left, value, level + 1);
  if (leftLevel != -1) {
    return leftLevel;
  }

  // If the code does not fin it on the left call itselft to the right 
  return findLevelRecursive(node->right, value, level + 1);
}

// updateRelations
void Tree::updateRelations() const {
  updateRelationsRecursive(this->root);
  std::cout << std::endl;
}
```

<p><a href="#MM">Back to main menu</a></p>

<br><br>

<h2 id="IE">Import and Export</h2>
<p>This Part is when the user decide to save the Tree on a file in order to printed or used on another time the functions **Import and Export** can be posible that</p>
<p align="center"><img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/10.png?raw=true" alt="Import and Export">
</p>
<h3>Export a Tree  </h3><p align="center">We save a file called **"FamilyTree"** with one value save it as a type FamilyTree.**csv** to save it and used it </p>
<p align="center"><img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/11.png?raw=true" alt="Import and Export"></p>
<p>The code for saving this file using the library **Fstream**  to reach the right place to save and used on another time</p>

```C++
void ExportInorderPeopleFromVector(const std::string& fileName,
                                   std::vector<Person>& personCollection) {
  std::fstream peopleFile;
  peopleFile.open(fileName, std::ios::out);

  if (!peopleFile.is_open()) {
    std::cout << std::endl
              << "\x1b[31mError trying opening this file: \x1b[0m" << fileName
              << std::endl;
    peopleFile.close();
    return;
  }

  for (const auto& element : personCollection) {
    peopleFile << element.id << "," << element.first_name << ","
               << element.last_name << "," << element.gender << ","
               << element.father << "," << element.mother << "\n";
  }

  peopleFile.close();
```
<h3>Import a Tree  </h3>
<p> This function takes one of the files name and has the same type of file **.csv** to reach it on the same folder as the repository was save and **File systme** to  be possible to write the name of the file and open it </p>
<p align="center"><img width="500" height="300" src="https://github.com/diegoschavez/practica_readme/blob/main/PED/12.png?raw=true" alt="Import and Export"></p>

<p> Opening the file and getting all the info for each data of the Structure save it counting each part </p>

```C++
void GetInorderPeopleFromFile(const std::string& fileName,
                              std::vector<Person>& personCollection) {
  std::fstream peopleFile;
  peopleFile.open(fileName, std::ios::in);

  if (!peopleFile.is_open()) {
    std::cout << std::endl
              << "\x1b[31mError trying opening this file: \x1b[0m" << fileName
              << std::endl;
    return;
  }
std::string currentLine;
  Person currentPerson;
  std::string auxConvertion;
  std::cout << std::endl
            << "\x1b[32mFile data received\x1b[0m" << std::endl
            << std::endl;
  while (std::getline(peopleFile, currentLine)) {
    std::stringstream currentLineStream(currentLine);
    std::getline(currentLineStream, auxConvertion, ',');
    currentPerson.id = std::stoi(auxConvertion);
    auxConvertion.clear();
    std::getline(currentLineStream, currentPerson.first_name, ',');
    std::getline(currentLineStream, currentPerson.last_name, ',');
    std::getline(currentLineStream, auxConvertion, ',');
    currentPerson.gender = auxConvertion[0];
    auxConvertion.clear();
    std::getline(currentLineStream, auxConvertion, ',');
    currentPerson.father = std::stoi(auxConvertion);
    auxConvertion.clear();
    std::getline(currentLineStream, auxConvertion, ',');
    currentPerson.mother = std::stoi(auxConvertion);
    std::cout << currentPerson << std::endl;
    personCollection.push_back(currentPerson);
  }

  peopleFile.close();
```


<p><a href="#MM">Back to main menu</a></p>
