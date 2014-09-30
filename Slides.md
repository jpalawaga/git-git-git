lll





 ____________
|____    ____|
     |  |
     |  |
     |  |
     |  |
 ____|  |____
|____________| NTRODUCTION TO GIT









Page 2



We're all familiar with this brilliant naming convention:


Coverletter.doc
Coverletter.doc.2
Coverletter.doc.bak
Coverletter.docx
Coverletter_FINAL.doc
Coverletter_NEWEST.doc
Coverletter_VERY_NEWEST.doc
Coverletter_no_references.doc
Coverletter_2_references.doc






End of page 2
Page 3 


Or, more recently, this...

    driver.cpp
    driver.cpp.back


Or maybe, inside one of those files...

    [ a bunch of production-quality code]

    /* int signal = 0;
    switch (input) {
        case 1:
        case 2:
        case 3:
            ...
   }*/


End of page 3 
Page 4 


Or, more recently, this...

    driver.cpp
    driver.cpp.back


Or maybe, inside one of those files...

    [ a bunch of production-quality code]

    /* int signal = 0;
    switch (input) {
        case 1:
        case 2:
        case 3:
            ...
   }*/


End of page 4 
 #########################################################   5/20   ########



DCVS

















End of page 2
 #########################################################   5/20   ########

 Branching in git               $> git branch NewFile 
  Original State                $> git checkout NewFile

                                                master  
                master*                         NewFile*
                 Head                            HEAD
                  |                                |
      _           _                    _           _
    /   \       /   \                /   \       /   \ 
   |  A  | --> |  B  |              |  A  | --> |  B  |
    \___/       \___/                \___/       \___/

 $> git commit 
                            HEAD
                master     NewFile
                  |           |
      _           _           _
    /   \       /   \       /   \
   |  A  | --> |  B  | --> |  C  |
    \___/       \___/       \___/
                                                                            EOP
 #########################################################   5/20   ########

 $> git commit 
                            HEAD
                master     NewFile*
                  |           |
      _           _           _
    /   \       /   \       /   \
   |  A  | --> |  B  | --> |  C  |
    \___/       \___/       \___/
 
 $> git checkout master 
 $> git commit           
      _           _              _
    /   \       /   \          /   \
   |  A  | --> |  B  | -----> |  C  | -- NewFile
    \___/       \___/  \       \___/
                        \        _
                         \     /   \ 
                          +-> |  D  | -- master*
                               \___/      HEAD

                                                                            EOP
 #########################################################   5/20   ########

 $> git merge NewFile 
                                               master*
                              NewFile           HEAD
                                 |               |
      _           _              _               _
    /   \       /   \          /   \           /   \
   |  A  | --> |  B  | -----> |  C  | -----+> |  E  | 
    \___/       \___/  \       \___/      /    \___/
                        \        _       /
                         \     /   \    /
                          +-> |  D  | -+ 
                               \___/    

                                                                            EOP
