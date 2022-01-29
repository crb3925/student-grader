

'student-grader'
-------------

Tired of manually compiling students' <b>C++</b> code submissions, and testing each individual input to the output? This Python script helps by automating the process.

Included are tests for certain assignments as they come in.

## Requirements

Software:
- Usage requires Python V3+. Dependent on 'difflib', 'ast' and 'argparse'.

A sample <i>test_assignment.txt</i> file might look like this:
```
{"compilation_line": 'g++ {stu_name}/assignment_1.cpp -o {stu_name}/{stu_name}',
 "test_params":  ["1\n2\n-1\n",
			      "1\n2\n1\n",
		          "1\n2\n3\n"],
 "test_output": [u'a: b: c: Correct output is 2\n',
				 u'a: b: c: Correct output is 4\n',
				 u'a: b: c: Correct output is 6\n']
}
```
It is based on a python Dictionary. The compilation line is the line executed to compile the assignment, and can be modified to accompany headers and more flags.  {stu_name} is the identified folder with the submission.
test_params and test_output should be lists of strings, which convey the std::cin and std::cout input and the expected output. test_params[0] corresponds to the input for test_output[0], etc...

Process pauses and waits for the user to hit enter before continuing to the next folder


## Sample Usage

Take the provided directory form below:
```
main_folder/
+---  compile_test_submissions.py
+---  tests/
|    +--- test_assignment1.txt
|    +--- test_assignment2.txt
|            ...
+--- student_submissions/
     +--- student_name_1/
     |     +--- assignment_1.cpp
     +--- student_name_2/
     |     +--- assignment_1.cpp
    ...
```

The code can be ran on this sample directory with the following command, where <i>'test_for_assignment_1.txt'</i> is a file containing the information for compiling and testing <i>assignment_1.cpp</i>.

```
python ./compile_test_submissions.py -r /tests/test_for_assignment_1.txt ~/student_submissions
```
