### Octave Notes

#### Initiation
To initiate Octave, use the following command within terminal:
``` Octave
  octave-cli
```
The terminal will look like the following:
``` Octave
  octave:2> some-command
```
The prefix (prompter) can be altered using the following command:
``` Octave
  PS1('>> ');
```
Which results in the following:
``` Octave
  >> some-command
```
Obviously, other symbols can be used, but '>>' is fairly standard.

#### Basics
Note, the prefix '>> ' is not coded, it is the same as the normal terminals '$ ' - it is a prompter. Addition is done by simply using the '+' symbol and pressing enter(return):
``` Octave
  >> 5+6
  ans =  11
```
Subtraction:
``` Octave
  >> 10-6
  ans =  4
```
Multiplication:
``` Octave
  >> 5*6
  ans =  30
```
Division:
``` Octave
  >> 1/2
  ans =  0.50000
```
Exponents:
``` Octave
  >> 2^3
  ans =  8
```
Comments:
``` Octave
  >> 5+6 % This is a comment
  ans =  11
```
Logical operations can also be performed. The operation '==' is the equality operator and '~=' the not equals operator:
``` Octave
  >> 1 == 2 % False
  ans =  0
  >> 1 == 1 % True
  ans =  1
  >> 1 ~= 2 % True
  ans =  1
```
There are also and, or and and/or operators:
``` Octave
  >> 0 && 1 % AND
  ans =  0
  >> 0 || 1 % OR
  ans =  1
  >> xor(1,0) % AND/OR
  ans =  1
```
Variables:
``` Octave
  >> a = 5 % This will print after enter
  a =  5
  >> a = 5; % The semicolon stops printing
  >> b = 'hello world'; % String declaration
  >> b
  b =  'hello world'
  >> c = (3>=1) % Should return 1 for TRUE
  c =  1
  >>
```
Printing (similar to C):
``` Octave
  >> a = pi;
  >> a
  a =  3.1416
  >> disp(a);
   3.1416
  >> disp(sprintf('2 decimals: %0.2f', a))
  2 decimals: 3.14
  >> disp(sprintf('6 decimals: %0.6f', a))
  2 decimals: 3.141593
```
Precision:
``` Octave
  >> a = pi
  a =  3.1416
  >> format long
  >> a
  a =  3.141592653589793
  >> format short
  a =  3.1416
```
Matrices:
``` Octave
  >> A = [1 2; 3 4; 5 6]
  A =

   1   2
   3   4
   5   6

  >> A = [1 2; % Press return
  > 3 4;
  > 5 6]
  A =

   1   2
   3   4
   5   6

  >>
```
Vectors:
``` Octave
  >> V = [1 2 3]
  V =

   1   2   3

  >> V = [1; 2; 3]
  V =

   1
   2
   3

  >>
```
Generate matrix/vector using increments:
``` Octave
  >> V = 1:0.1:1.5
  V =

    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000

  >> V = 1:5
  V =

   1   2   3   4   5

  >>
```
Initialised matrix/vector:
``` Octave
  >> ones(2, 3)
  ans =

   1   1   1
   1   1   1

  >> zeros(3, 2)
  ans =

   0   0
   0   0
   0   0

  >> 2*ones(2,3)
  ans =

   2   2   2
   2   2   2

  >> rand(3, 3)
  ans =

     0.413530   0.048008   0.602770
     0.941902   0.049522   0.723525
     0.352443   0.789396   0.821921

  >>
```
You can also use the Gaussian random variable:
``` Octave
  >> randn(1, 3)
  ans =

   1.1157  -1.7531   1.2317

  >>
```
Initialise a vector using 'randn' and then plot a histogram of the results:
``` Octave
  >> w = 2*randn(1, 10000);
  >> hist(w)
```
This will give popup window with the diagram. To increase the number of bins, to say 'x', simply do the following:
``` Octave
  >> w = 2*randn(1, 10000);
  >> hist(w, x)
```
Identity matrix:
``` Octave
  >> I = eye(4)
  I =

  Diagonal Matrix

     1   0   0   0
     0   1   0   0
     0   0   1   0
     0   0   0   1

  >>
```
HELP:
``` Octave
  >> help rand % q to quit
  >> help eye
  >> help help
```

#### Further
The 'size' command gives you the dimensions of a vector - note this function returns a matrix also:
``` Octave
  >> I = eye(4);
  >> size(I)
  ans =

     4   4

  >> sz = size(I);
  >> sz
  sz =

     4   4

  >>
```
The number of rows and columns of a given matrix can be found as follows:
``` Octave
  >> T = ones(2, 3)
  T =

   1   1   1
   1   1   1

  >> size(T,1) % num of rows
  ans =  2
  >> size(T,2) % num of columns
  ans =  3
  >>
```
The size of the largest dimension can be found by using the function 'length':
``` Octave
  >> length(T) % size of largest dim of T
  ans =  3
  >>
```
To load in some data, first locate to the directory containing the data and then the following:
``` Octave
  >> load some-data.dat % or...
  >> load('some-data.dat') % this is equiv
```
The second one simply converts the file name to a string.

To see which variables are currently being stored in memory, use the 'who' command:
``` ocatve
  >> who
  Variables in the current scope:

  I    T    ans  sz   w

  >>
```
and for a more detailed output containing types and precision, use the 'whos' command:
``` Octave
  >> whos
  Variables in the current scope:

     Attr Name        Size                     Bytes  Class
     ==== ====        ====                     =====  =====
          I           4x4                         32  double
          T           2x3                         48  double
          ans         1x41                        41  char
          sz          1x2                         16  double
          w           1x10000                  80000  double

  Total is 10065 elements using 80137 bytes

  >>
```
To remove a variable from memory (deallocate), simply use the 'clear var' command:
``` Octave
  >> clear T
  >> whos
  Variables in the current scope:

     Attr Name        Size                     Bytes  Class
     ==== ====        ====                     =====  =====
          I           4x4                         32  double
          ans         1x41                        41  char
          sz          1x2                         16  double
          w           1x10000                  80000  double

  Total is 10059 elements using 80089 bytes

  >>
```
Alternatively, 'clear' by itself will delete all variables from the workspace.

To save data, say for example a vector, simply use the command 'save filename.extension var -options':
``` octave
  >> data = rand(1, 10)
  data =

     0.91028   0.28995   0.80792   0.92347   0.80171   0.88368   0.66139   0.69487   0.74583   0.91403

  >> save some-data.dat data
  >> save some-data.txt data -ascii
  >>
```
Other extensions, such as .mat for MATLAB can be used (saves in binary format). The -ascii flag saves the data as raw data, whereas without, it also contains other information, such as creation data, variable name, data type ect.

Data can be indexed by using var(x,y) for index (x,y) of data var:
``` Octave
  >> V = [1 2; 3 4; 5 6]
  V =

     1   2
     3   4
     5   6

  >> V(3,2)
  ans =  6
  >> V(1,1)
  ans =  1
  >>
```
Or, you can select entire columns and rows using colon:
``` Octave
  >> V(:,1)
  ans =

     1
     3
     5

  >> V(:,2)
  ans =

     2
     4
     6

  >>
```
You can also specify certain columns/rows, for example:
``` octave
  >> V([1 3],:)
  ans =

     1   2
     5   6

  >> V([1 2], [2])
  ans =

     2
     4

  >>
```
You can assign entire columns/rows:
``` octave
  >> V(:, 2) = [7; 8; 9]
  V =

     1   7
     3   8
     5   9

  >>
```
You can also append:
``` octave
>> V = [V, [10; 11; 12]]
  V =

      1    7   10
      3    8   11
      5    9   12

  >>
```
Special function, places all elements in a matrix into a column vector:
``` octave
  >> V(:) % all elements go into column vector
  ans =

      1
      3
      5
      7
      8
      9
     10
     11
     12

  >>
```
Horizontal (space or ,) and vertical (;) concatenation:
``` octave
  >> M = [1 2; 3 4; 5 6]
  M =

     1   2
     3   4
     5   6

  >> N = 3*M
  N =

      3    6
      9   12
     15   18

  >> O = [M N]
  O =

      1    2    3    6
      3    4    9   12
      5    6   15   18

  >> O = [M; N]
  O =

      1    2
      3    4
      5    6
      3    6
      9   12
     15   18

  >>
'''
