# Merchant's Guide to the Galaxy

It is a python based program used to make the task of converting numbers and units simpler in galaxy.
  - Python 2.7 is used here.
  - Program has been tested with sufficient unittest test cases.

### Syntax for using from command line
    python galaxy_guide.py <input_file>
** input_file = file to read input from, (default is input.txt) **
    
### Convention for input file:
1. All data read from input file are **case-sensitive**
2. Input can read only in the specified format as given below:
    1. (unit in lower case) is ( symbols from I,V,X,L,C,D,M )
    2. (unit1 unit2 unit3 .. unitn) (metal name with first alphabet capital) is (price) Credits
    3. how much is (unit1 unit2 unit3 .. unitn) ?
    4. how many Credits is (unit1 unit2 unit3 .. unitn) (metal name with first alphabet capital) ?
3. ** The sequence in which input are passed also matters. ** Input file should contain Input type 1 (as given above) followed by type2, the question (type 3 and 4) can be in any order but should be only after type1 and type2. Refer to input.txt to get a clear idea.
4. If any input question is invalid it will generate a error statement in output.
5. If the conversion input is wrong, it will exit the program by printing the line which has error.
6. Default input file input.txt has been attached.

### Design and code flow
1. Module roman_to_number contains the logic to convert input roman number to base 10 english number.
    * __mapping__ dictionary contain the mapping of symbols to numbers.
    * __roman_to_number__ method takes a roman string, validates it by calling __is_valid__ method and converts it into
   appropriate number.
    * __is_valid__ method contains the logic to check if the input roman string is valid or not. It uses various regular
   expression to check the input step-by-step.
2. galaxy_guide module reads the input file line-by-line, checks it using the regular expression constructed dynamically
   and creates a list of output.
    * This module contains a class **GalaxyGuide**, while instantiating this class, name of input file can be passed or the default input.txt file will be used.
    * The index method reads input file line-by-line, make use of **current_type** property to call the appropiate the method.
    * _input_type1 and _input_type2 are used to validate and extract information from type1 and type1 line
    * _question_type1 and _question_type2 are used to validate and generate output from question1 and question2 line
3. KISS (keep it smart and simple) & DRY (Do not repeat yourself) principle has been tried to followed through out the
    program to keep the logic simple and at one place
4. [PEP 0008 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008) has been used to maintain the coding convention consistent.


### Unit test
1. Python unittest module has been used for testing.
2. Unit test for module roman_to_number has been include in file test_r_to_n.py . Care has been taken place to check again different conditions. It can be runned using below command line statement.
        python test_r_to_n.py
3. Unit test for module galaxy_guide has been include in test_galaxy_guide.py . All different input files are present in test_inputs file. It can be runned using below command line statement.
        python test_galaxy_guide.py

Thanks for using it.



    
