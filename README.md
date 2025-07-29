# Yaml-Generator-MSCG
Yaml Generator for OpenMSCG by Ace.

Description
-----------

The ``cgyaml.py`` reads the user-defined mapping for residues and generate the yaml file used by cgmap. It also generate the CG coordinate file based on the input AA coordinates. 

Mapping of nonprotein moleculeS/residues is based on atom indices (starting from 0) in the molecule/residue.
<br/>**Example: 2-bead methanol**
<pre> 
    CH3
    [0, 1, 2, 3]
    OH
    [4, 5]
</pre>

Proteins are treated as one "molecule". Mapping of proteins is based on absolute protein residue indices (starting from 0).

<br/><br/>**Example: heterodimer**
<br/>chain A resid: 1-10; chain B resid: 2-7
chain A start from 0
<pre>
    P0
    [0, 3, 2, 1]
    P1
    [4, 9]
    P2
    [7, 6]
    P4
    [5, 8]
</pre>

chain B start from 10 because chain A has 10 residues
<pre>
    P5
    [10, 13]
    P6
    [12, 11]
    P7
    [14]
</pre>

Support random order of atom/residue indices, partial mapping (not all the atoms has to be defined in the mapping)

Protein beads are mapped by all the atoms in the given residues

Examples are provided in Examples/


Usage
-----

Syntax of running ``cgyaml.py`` 

    General arguments:
      -h, --help            show this help message and exit
      -v, --verbose       being noisy

    Required arguments:
       --aa                   AA coordinate file, like .pdb or .gro. Need to contain residue information
       --mapfile              YAML file indexing all mapping files. See examples. 


    Optional arguments:
      --dir                   Working directory
      --yaml                 File name of the output yaml mapping file
      --cg                    File name of the output CG coordinate file
      --prefix              Prefix of the bead names of protein beads
      --loop                 Offset of the protein's repeating pattern. Homomultimer as an example, this is # of amino acids in a chain. Set to -1 to turn off (default: -1)
      --smart               Whether try to map the undefined protein residues with the existing definition. Has to be turned off when --loop is not -1. (default: False)

'''
