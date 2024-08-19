# Excel POC - Vanilla JS 😊

## notes...

℗ Two-Way binding _____
                                        |
                                        |___ Data change in Storage.
                                        |___ UI change.


℗ Storage _____
                          |
                          |___________________
                          |                                        |
                          |    each cell represents    |
                          |          an object               |
                          |    with some properties   |
                          |___________________|  ___ (100 X 26) matrix


℗ Access active cell _____
                                         |
                                         |___ Decode (row_id, column_id) from left-top corner Address cell.
                                         |___ Change in cell accordingly, & also in the DB.


℗ Save cell value _____ addEventListener('blur', () => { // save in DB}) //blur accesses the previous value before click


℗ Formula evaluation _____
                                           |
                                           |___ Independent expression. (just evaluate on pressing enter key.)
                                           |___ Dependent expression. (first decode dependent cells value, then evaluate.)


℗ Child dependency preservation _____
                                                             |
                                                             |___ Recursively modify all childrens using DFS.
                                                             |___ So, every cell should have a property for childrens.
                                                             |___ cell = { ..., childrens : [] };


℗ Cycle detection in Directed Graph _____ 
                                                                  |
                                                                  |___ If any single cycle detected, we need to stop .
                                                                  |___ 2 arrays (visited[F] & dfsStack[F]).
                                                                  |___ when visiting node, visited(node) = T && dfsStack(node) = T, when returning only dfsStack(node) = F
                                                                  |___ if ( visited(node) && dfsStack(node) ) it's cycle.
                                                                  |___ if ( visited(node) ) return;


℗ Graph representation _____
                                               |
                                               |___ storage 
                                                                   |
                                                                   |___ 3D array, each cell in matrix will be an array.
                                                                   |___ each array-cell will contain array of childrens.
                                                                   |___ each cell -> [[0, 1], [row, col], ...];


℗ Trace Graph Cycle _____ 
                                          |
                                          |___ trace only the path, containing cycle, i.e. got from prev.
                                          |___ delay 
                                          |              |
                                          |              |___ Some delay for each cell for visibility.
                                          |              |___ Create and return new Promise.
                                          |
                                          |___ wait 
                                                        |
                                                        |___ Wait for user input, if want to see again.
                                                        |___ Use async await.


℗ Isollated sheet management _____ 
                                                         |
                                                         |___ Each sheet has diff DB matrix.
                                                         |___ Just override each cell value from DB.


℗ Cut-Copy-Paste _____ 
                                     |
                                     |___ Select start & end range cell.
                                     |___ Use ctrl + enter event.
                                     |___ If already 2 cell selected, remove 1 st cell & set 2nd as start.


℗ Download sheet _____ 
                                      |
                                      |___ Download in JSON format.
                                      |___ Use Blob to convert the json.


℗ Upload sheet _____ 
                                  |
                                  |___ Upload JSON file.
                                  |___ Use FileReader.


