# QSalign

1.INTRODUCTION
--------------------
Method for superposition of quaternary structures with multiple chains

2. SYSTEM REQUIREMENT
---------------------
Linux or Unix system is required

3. EXTERNAL PROGRAMS
---------------------

QSaling uses the program KPAX version 3 to run structure alignments. KPAX executable is supplied with this package.

4. STEPS FOR RUNNING QSalign
------------------------------

  Step 1.

    Download the archive “use_QSalign.tar.gz”      

  Step 2.

    unzip using the command:

    tar -xvfz XXXX.tar.gz

  Step 3.

    Make sure the folder “use_QSalign” contains the following files/folders:

     i)  00_EXE_KPAX_CORRES_modified.pl
    ii)  QSalign.pl
   iii)  kpax.pm
    iv)  target_file.txt (sample file)
     v)  README.txt
    vi)  folder 'bin' which contains 'kpax' executables
   vii)  folder 'pdb' which contains query and target pdb files from PDB
  viii)  folder 'pdb_pisa' which contains target pdb files from PISA (if any)
    ix)  folder 'pdb_split' which contains the pdb files with chains splitted

  Step 4.

    Open “kpax.pm” and change the paths of the following folders according to where its is downloaded :

    i)   $BU_PDB    (all files from PDB)
    ii)  $BU_PISA   (all files from PISA, if any)
    iii) $BU_SPLIT  (files with chains splitted)
    
    Redundancy in chain names can be found at times in a file provided by PDB, make sure to make the chain names uniq.
    Assemblies with renamed (uniq) chain names can be obtained from  http://shmoo.weizmann.ac.il/elevy/3dcomplexV5/Download2.cgi
    
    All assemblies from PDB, PISA and splitted files used in 3Dcomplex can be obtained from 
    http://shmoo.weizmann.ac.il/elevy/3dcomplexV5/dataV5/QSalign_exe.html

    [OPTIONAL]

    iv) $T_CUT  – This is the TM-score cut-off that shows how good is the alignment and hence how similar are two structures. User can change the value in the range (0-1); 0 – no match , 1 – perfect match (identical structures).  Default value given is 0.65, for finding structural homologs it should be atleast 0.5.

    After making the changes save the file “kpax.pm”

  Step 5. [OPTIONAL]

    By default the folder “BU_PISA” contains only the top solution from PISA, if one wants to use few more solutions from PISA, then run PISA from CCP4 Program suite  (http://www.ccp4.ac.uk/index.php) and copy the assemblies as XXXX_p1.pdb (already present), XXXX_p2.pdb etc. into the folder BU_PISA. Also add the entries in the name list file “pdb_pisa.txt”

  Step 6.
  
   Run  "QSalign.pl" with the full path of the query and number of subunits the query has and the target file containg 4 letter target code and corresponding number of subunits. (a sample target file is provided)
       
        perl QSalign.pl /home/XXXX.pdb 4 target_file.txt

    Run time depends upon the size of the query, T_CUT, and number of targets, can take ~2mins to few hours for each run.

  Step 7.

    Output generated in the folder “QSalign_results” as “XXXX.QSalign_out”

    Gives the list of structures found similar to the query (if any), along with respective TM-Score and few more attributes as generated from KPAX.

    A log folder “QSalign_LOG” is also generated containing intermediate files.


  TIPS:

    Run one query at a time

    Start with the default T_CUT of 0.65, if very less or no structures found in the output, try with less values.


5. TRY THE EXAMPLE RUN (all required files are supplied):
----------------------------------------------------------

    perl QSalign.pl ./pdb/5rub_1.pdb 2 target_file.txt
    

If you have any problem or suggestion, please contact:
emmanuel.levy@weizmann.ac.il OR sucharita.dey@weizmann.ac.il


