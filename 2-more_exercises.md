
# Python review: More exercises

This notebook continues the review of Python basics. A key concept is that of a _nested_ data structure. For example, the first code cell will define a 2-D "array" as a list of lists.


```python
%load_ext autoreload
%autoreload 2
```

Consider the following dataset of exam grades, organized as a 2-D table and stored in Python as a "list of lists" under the variable name, `grades`.


```python
grades = [
    # First line is descriptive header. Subsequent lines hold data
    ['Student', 'Exam 1', 'Exam 2', 'Exam 3'],
    ['Thorny', '100', '90', '80'],
    ['Mac', '88', '99', '111'],
    ['Farva', '45', '56', '67'],
    ['Rabbit', '59', '61', '67'],
    ['Ursula', '73', '79', '83'],
    ['Foster', '89', '97', '101']
]

grades
```




    [['Student', 'Exam 1', 'Exam 2', 'Exam 3'],
     ['Thorny', '100', '90', '80'],
     ['Mac', '88', '99', '111'],
     ['Farva', '45', '56', '67'],
     ['Rabbit', '59', '61', '67'],
     ['Ursula', '73', '79', '83'],
     ['Foster', '89', '97', '101']]



**Exercise 0** (`students_test`: 1 point). Complete the function `get_students` which takes a nested list `grades` as a parameter and reutrns a new list, `students`, which holds the names of the students as they from "top to bottom" in the table. 
- **Note**: the parameter `grades` will be similar to the table above in structure, but the data will be different.


```python
def get_students(grades):
    ###
    ### YOUR CODE HERE
    list_len = len(grades)
    print (list_len)
    return[item[0] for item in grades[1:]]
    ###

```

The demo cell below should display `['Thorny', 'Mac', 'Farva', 'Rabbit', 'Ursula', 'Foster']`.


```python
students = get_students(grades)
students
```

    7





    ['Thorny', 'Mac', 'Farva', 'Rabbit', 'Ursula', 'Foster']



The test cell below will check your solution against several randomly generated test cases. If your solution does not pass the test (or if you're just curious), you can look at the variables used in the latest test run. They are automatically imported for you as part of the test.

- `input_vars` - Dictionary containing all of the inputs to your function. Keys are the parameter names.
- `original_input_vars` - Dictionary containing a copy of all the inputs to your function. This is useful for debugging failures related to your solution modifying the input. Keys are the parameter names.
- `returned_output_vars` - Dictionary containing the outputs your function generated. If there are multiple outputs, the keys will match the names mentioned in the exercrise instructions.
- `true_output_vars` - Dictionary containing the outputs your function **should have** generated. If there are multiple outputs, the keys will match the names mentioned in the exercrise instructions.

All of the test cells in this notebook will use the same format, and you can expect a similar format on your exams as well.


```python
# `students_test`: Test cell
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_0()
for _ in range(20):
    try:
        tester.run_test(get_students)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    6
    6
    7
    5
    11
    8
    9
    11
    7
    8
    8
    9
    6
    7
    7
    6
    9
    10
    6
    7
    Passed. Please submit!


**Exercise 1** (`assignments_test`: 1 point). Complete the function `get_assignments`. The function takes `grades` (a nested list structured similarly to `grades` above) as a parameter. It should return a new list `assignments` which holds the names of the class assignments. (These appear in the descriptive header element of `grades`.)


```python
def get_assignments(grades):
    ###
    ### YOUR CODE HERE
    new_grades = []
    new_grades = grades[0][1:]
    return new_grades
    ###

```

The demo cell below should display `['Exam 1', 'Exam 2', 'Exam 3']`


```python
assignments = get_assignments(grades)
assignments
```




    ['Exam 1', 'Exam 2', 'Exam 3']



The following test cell will check your function against several randomly generated test cases.


```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_1()
for _ in range(20):
    try:
        tester.run_test(get_assignments)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Passed. Please submit!


**Exercise 2** (`grade_lists_test`: 1 point). Complete the function for `build_grade_lists`, again taking `grades` as a parameter. The function should return a new _dictionary_, named `grade_lists`, that maps names of students to _lists_ of their exam grades. The grades should be converted from strings to integers. For instance, `grade_lists['Thorny'] == [100, 90, 80]`.


```python
# Create a dict mapping names to lists of grades.
def build_grade_lists(grades):
    ###
    ### YOUR CODE HERE
    new_List = {}
    for Length in grades[1:]:
        new_List[Length[0]] = [int(g) for g in Length[1:]]
        
    return new_List
    ###

```

The demo cell below should display
```
{'Thorny': [100, 90, 80],
 'Mac': [88, 99, 111],
 'Farva': [45, 56, 67],
 'Rabbit': [59, 61, 67],
 'Ursula': [73, 79, 83],
 'Foster': [89, 97, 101]}
```


```python
grade_lists = build_grade_lists(grades)
grade_lists
```




    {'Thorny': [100, 90, 80],
     'Mac': [88, 99, 111],
     'Farva': [45, 56, 67],
     'Rabbit': [59, 61, 67],
     'Ursula': [73, 79, 83],
     'Foster': [89, 97, 101]}




```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_2()
for _ in range(20):
    try:
        tester.run_test(build_grade_lists)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Passed. Please submit!


**Exercise 3** (`grade_dicts_test`: 2 points). Complete the function `build_grade_dicts`, again taking `grades` as a parameter and returning new dictionary, `grade_dicts`, that maps names of students to _dictionaries_ containing their scores. Each entry of this scores dictionary should be keyed on assignment name and hold the corresponding grade as an integer. For instance, `grade_dicts['Thorny']['Exam 1'] == 100`. You may find solutions to earlier exercises useful for completing this one. Feel free to use them!


```python
def build_grade_dicts(grades):
    ###
    ### YOUR CODE HERE
    assignments = get_assignments(grades)
    
    grade_dicts = {}
    
    for Length in grades[1:]:
        grade_dicts[Length[0]] = dict(zip(assignments, [int(g) for g in Length[1:]]))

    return grade_dicts
    ###

```

The demo cell below should display
```
{'Thorny': {'Exam 1': 100, 'Exam 2': 90, 'Exam 3': 80},
 'Mac': {'Exam 1': 88, 'Exam 2': 99, 'Exam 3': 111},
 'Farva': {'Exam 1': 45, 'Exam 2': 56, 'Exam 3': 67},
 'Rabbit': {'Exam 1': 59, 'Exam 2': 61, 'Exam 3': 67},
 'Ursula': {'Exam 1': 73, 'Exam 2': 79, 'Exam 3': 83},
 'Foster': {'Exam 1': 89, 'Exam 2': 97, 'Exam 3': 101}}
 ```


```python
grade_dicts = build_grade_dicts(grades)
grade_dicts
```




    {'Thorny': {'Exam 1': 100, 'Exam 2': 90, 'Exam 3': 80},
     'Mac': {'Exam 1': 88, 'Exam 2': 99, 'Exam 3': 111},
     'Farva': {'Exam 1': 45, 'Exam 2': 56, 'Exam 3': 67},
     'Rabbit': {'Exam 1': 59, 'Exam 2': 61, 'Exam 3': 67},
     'Ursula': {'Exam 1': 73, 'Exam 2': 79, 'Exam 3': 83},
     'Foster': {'Exam 1': 89, 'Exam 2': 97, 'Exam 3': 101}}




```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_3()
for _ in range(20):
    try:
        tester.run_test(build_grade_dicts)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Passed. Please submit!


**Exercise 4** (`avg_grades_by_student_test`: 1 point). Complete the function `build_avg_by_student`, taking `grades` as a parameter and returning a dictionary named `avg_by_student` that maps each student to his or her average exam score. For instance, `avg_grades_by_student['Thorny'] == 90`. You may find solutions to earlier exercises useful for completing this one. Feel free to use them!

> **Hint.** The [`statistics`](https://docs.python.org/3.5/library/statistics.html) module of Python has at least one helpful function.


```python
# Create a dict mapping names to grade averages.
def build_avg_by_student(grades):
    ###
    ### YOUR CODE HERE
    
    list_grades = build_grade_lists(grades)
    from statistics import mean
    return{n: mean(G) for n,G in list_grades.items()}
    ###

```

The demo cell below should display
```
{'Thorny': 90,
 'Mac': 99.33333333333333,
 'Farva': 56,
 'Rabbit': 62.333333333333336,
 'Ursula': 78.33333333333333,
 'Foster': 95.66666666666667}
```


```python
avg_grades_by_student = build_avg_by_student(grades)
avg_grades_by_student
```




    {'Thorny': 90,
     'Mac': 99.33333333333333,
     'Farva': 56,
     'Rabbit': 62.333333333333336,
     'Ursula': 78.33333333333333,
     'Foster': 95.66666666666667}




```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_4()
for _ in range(20):
    try:
        tester.run_test(build_avg_by_student)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Passed. Please submit!


**Exercise 5** (`grades_by_assignment_test`: 2 points). Complete the function `build_grade_by_asn`, which takes `grades` as a parameter and returns a dictionary named `grade_by_asn`, whose keys are assignment (exam) names and whose values are lists of scores over all students on that assignment. For instance, `grades_by_assignment['Exam 1'] == [100, 88, 45, 59, 73, 89]`. You may find solutions to earlier exercises useful for completing this one. Feel free to use them!


```python
def build_grade_by_asn(grades):
    ###
    ### YOUR CODE HERE
    assignments = get_assignments(grades)
    grades_by_assignments = {}
    
    for i,v in enumerate(assignments):
        grades_by_assignments[v] = [int (Length [i + 1]) for Length in grades[1:]]
        
    return grades_by_assignments
    ###

```

The demo cell below should display
```
{'Exam 1': [100, 88, 45, 59, 73, 89],
 'Exam 2': [90, 99, 56, 61, 79, 97],
 'Exam 3': [80, 111, 67, 67, 83, 101]}
```


```python
grades_by_assignment = build_grade_by_asn(grades)
grades_by_assignment
```




    {'Exam 1': [100, 88, 45, 59, 73, 89],
     'Exam 2': [90, 99, 56, 61, 79, 97],
     'Exam 3': [80, 111, 67, 67, 83, 101]}




```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_5()
for _ in range(20):
    try:
        tester.run_test(build_grade_by_asn)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Passed. Please submit!


**Exercise 6** (`avg_grades_by_assignment_test`: 1 point). Complete the function `build_avg_by_asn`, which takes `grades` as a parameter and returns a dictionary, `avg_by_asn`, which maps each exam to its average score. You may find solutions to earlier exercises useful for completing this one. Feel free to use them!


```python
# Create a dict mapping items to average for that item across all students.
def build_avg_by_asn(grades):
    ###
    ### YOUR CODE HERE
    from statistics import mean
    grades_by_assignment = build_grade_by_asn(grades)
    
    return{n: mean(G) for n,G in grades_by_assignment.items()}
    ###

```

The demo cell below should display
```
{'Exam 1': 75.66666666666667,
 'Exam 2': 80.33333333333333,
 'Exam 3': 84.83333333333333}
```


```python
avg_grades_by_assignment = build_avg_by_asn(grades)
avg_grades_by_assignment
```




    {'Exam 1': 75.66666666666667,
     'Exam 2': 80.33333333333333,
     'Exam 3': 84.83333333333333}




```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_6()
for _ in range(20):
    try:
        tester.run_test(build_avg_by_asn)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Passed. Please submit!


**Exercise 7** (`rank_test`: 2 points). Complete the function `get_ranked_students` which takes `grades` as an argument and returns a new list, `ranked_students`, which contains the names of students in order by _decreasing_ score. That is, `ranked_students[0]` should contain the name of the top student (highest average exam score), and `ranked_students[-1]` should have the name of the bottom student (lowest average exam score). You may find solutions to earlier exercises useful for completing this one. Feel free to use them!


```python
def get_ranked_students(grades):
    ###
    ### YOUR CODE HERE
    from statistics import mean
    
    ranked_students = []
    
    print('Grades = ', grades)
    
    exams = grades[0][1:]
    
    print('Exams = ', exams)
    
    students = [data[0] for data in grades[1:]]
    
    print('Students = ', students)
    
    avg_grades_by_studeents = []
    
    avg_grades_by_students = build_avg_by_student(grades)
    
    print("Average grades by student = ", avg_grades_by_students)
    
    rank = sorted (avg_grades_by_students, key=avg_grades_by_students.get, reverse = True)
    
    print('Rank = ', rank)
    
    return rank

```

The demo cell below shuould display `['Mac', 'Foster', 'Thorny', 'Ursula', 'Rabbit', 'Farva']`


```python
rank = get_ranked_students(grades)
rank
```

    Grades =  [['Student', 'Exam 1', 'Exam 2', 'Exam 3'], ['Thorny', '100', '90', '80'], ['Mac', '88', '99', '111'], ['Farva', '45', '56', '67'], ['Rabbit', '59', '61', '67'], ['Ursula', '73', '79', '83'], ['Foster', '89', '97', '101']]
    Exams =  ['Exam 1', 'Exam 2', 'Exam 3']
    Students =  ['Thorny', 'Mac', 'Farva', 'Rabbit', 'Ursula', 'Foster']
    Average grades by student =  {'Thorny': 90, 'Mac': 99.33333333333333, 'Farva': 56, 'Rabbit': 62.333333333333336, 'Ursula': 78.33333333333333, 'Foster': 95.66666666666667}
    Rank =  ['Mac', 'Foster', 'Thorny', 'Ursula', 'Rabbit', 'Farva']





    ['Mac', 'Foster', 'Thorny', 'Ursula', 'Rabbit', 'Farva']




```python
import nb_1_2_tester
tester = nb_1_2_tester.Tester_1_2_7()
for i in range(5):
    try:
        tester.run_test(get_ranked_students)
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
    except:
        (input_vars, original_input_vars, returned_output_vars, true_output_vars) = tester.get_test_vars()
        raise
print('Passed. Please submit!')
```

    Grades =  [['Student', 'Exam 1', 'Exam 2', 'Exam 3'], ['Jek Tono Porkins', '90', '76', '75'], ['Shaak Ti', '64', '82', '98'], ['Kit Fisto', '70', '76', '88'], ['Ki-Adi-Mundi', '50', '56', '82'], ['Luke Skywalker', '80', '72', '61'], ['Ben Quadinaros', '61', '73', '87']]
    Exams =  ['Exam 1', 'Exam 2', 'Exam 3']
    Students =  ['Jek Tono Porkins', 'Shaak Ti', 'Kit Fisto', 'Ki-Adi-Mundi', 'Luke Skywalker', 'Ben Quadinaros']
    Average grades by student =  {'Jek Tono Porkins': 80.33333333333333, 'Shaak Ti': 81.33333333333333, 'Kit Fisto': 78, 'Ki-Adi-Mundi': 62.666666666666664, 'Luke Skywalker': 71, 'Ben Quadinaros': 73.66666666666667}
    Rank =  ['Shaak Ti', 'Jek Tono Porkins', 'Kit Fisto', 'Ben Quadinaros', 'Luke Skywalker', 'Ki-Adi-Mundi']
    Grades =  [['Student', 'Exam 1', 'Exam 2', 'Exam 3', 'Exam 4'], ['IG-88', '97', '77', '82', '53'], ['Cordé', '66', '77', '54', '66'], ['Saesee Tiin', '55', '85', '60', '67'], ['Ackbar', '82', '82', '93', '99'], ['Finis Valorum', '66', '51', '87', '50'], ['Chewbacca', '65', '98', '84', '59']]
    Exams =  ['Exam 1', 'Exam 2', 'Exam 3', 'Exam 4']
    Students =  ['IG-88', 'Cordé', 'Saesee Tiin', 'Ackbar', 'Finis Valorum', 'Chewbacca']
    Average grades by student =  {'IG-88': 77.25, 'Cordé': 65.75, 'Saesee Tiin': 66.75, 'Ackbar': 89, 'Finis Valorum': 63.5, 'Chewbacca': 76.5}
    Rank =  ['Ackbar', 'IG-88', 'Chewbacca', 'Saesee Tiin', 'Cordé', 'Finis Valorum']
    Grades =  [['Student', 'Exam 1', 'Exam 2', 'Exam 3', 'Exam 4', 'Exam 5', 'Exam 6'], ['Han Solo', '94', '68', '56', '67', '82', '100'], ['Arvel Crynyd', '53', '77', '53', '85', '73', '94'], ['Poe Dameron', '86', '59', '60', '64', '54', '75'], ['Raymus Antilles', '50', '94', '79', '71', '65', '64']]
    Exams =  ['Exam 1', 'Exam 2', 'Exam 3', 'Exam 4', 'Exam 5', 'Exam 6']
    Students =  ['Han Solo', 'Arvel Crynyd', 'Poe Dameron', 'Raymus Antilles']
    Average grades by student =  {'Han Solo': 77.83333333333333, 'Arvel Crynyd': 72.5, 'Poe Dameron': 66.33333333333333, 'Raymus Antilles': 70.5}
    Rank =  ['Han Solo', 'Arvel Crynyd', 'Raymus Antilles', 'Poe Dameron']
    Grades =  [['Student', 'Exam 1', 'Exam 2', 'Exam 3', 'Exam 4', 'Exam 5', 'Exam 6'], ['Poggle the Lesser', '51', '56', '86', '89', '70', '80'], ['Wilhuff Tarkin', '69', '61', '95', '88', '73', '66'], ['Roos Tarpals', '84', '88', '94', '61', '84', '51'], ['Jar Jar Binks', '58', '76', '69', '91', '70', '51'], ['Taun We', '58', '64', '66', '84', '84', '56'], ['Qui-Gon Jinn', '92', '80', '100', '56', '58', '69'], ['Finis Valorum', '54', '56', '85', '58', '87', '71'], ['Zam Wesell', '63', '51', '54', '81', '65', '55'], ['Mas Amedda', '87', '73', '76', '69', '85', '95'], ['Adi Gallia', '52', '66', '86', '84', '93', '89'], ['Ki-Adi-Mundi', '97', '85', '58', '88', '70', '97']]
    Exams =  ['Exam 1', 'Exam 2', 'Exam 3', 'Exam 4', 'Exam 5', 'Exam 6']
    Students =  ['Poggle the Lesser', 'Wilhuff Tarkin', 'Roos Tarpals', 'Jar Jar Binks', 'Taun We', 'Qui-Gon Jinn', 'Finis Valorum', 'Zam Wesell', 'Mas Amedda', 'Adi Gallia', 'Ki-Adi-Mundi']
    Average grades by student =  {'Poggle the Lesser': 72, 'Wilhuff Tarkin': 75.33333333333333, 'Roos Tarpals': 77, 'Jar Jar Binks': 69.16666666666667, 'Taun We': 68.66666666666667, 'Qui-Gon Jinn': 75.83333333333333, 'Finis Valorum': 68.5, 'Zam Wesell': 61.5, 'Mas Amedda': 80.83333333333333, 'Adi Gallia': 78.33333333333333, 'Ki-Adi-Mundi': 82.5}
    Rank =  ['Ki-Adi-Mundi', 'Mas Amedda', 'Adi Gallia', 'Roos Tarpals', 'Qui-Gon Jinn', 'Wilhuff Tarkin', 'Poggle the Lesser', 'Jar Jar Binks', 'Taun We', 'Finis Valorum', 'Zam Wesell']
    Grades =  [['Student', 'Exam 1', 'Exam 2', 'Exam 3', 'Exam 4', 'Exam 5', 'Exam 6'], ['Plo Koon', '91', '94', '96', '55', '91', '83'], ['Ratts Tyerell', '64', '63', '65', '79', '91', '62'], ['R2-D2', '57', '76', '100', '101', '79', '89'], ['Han Solo', '83', '96', '79', '78', '95', '76'], ['Leia Organa', '92', '61', '54', '56', '101', '81'], ['Chewbacca', '78', '82', '60', '79', '81', '51'], ['Palpatine', '76', '99', '50', '53', '93', '56'], ['Bib Fortuna', '86', '72', '52', '75', '65', '71'], ['Owen Lars', '76', '80', '86', '96', '83', '94'], ['Lobot', '67', '97', '99', '101', '84', '98']]
    Exams =  ['Exam 1', 'Exam 2', 'Exam 3', 'Exam 4', 'Exam 5', 'Exam 6']
    Students =  ['Plo Koon', 'Ratts Tyerell', 'R2-D2', 'Han Solo', 'Leia Organa', 'Chewbacca', 'Palpatine', 'Bib Fortuna', 'Owen Lars', 'Lobot']
    Average grades by student =  {'Plo Koon': 85, 'Ratts Tyerell': 70.66666666666667, 'R2-D2': 83.66666666666667, 'Han Solo': 84.5, 'Leia Organa': 74.16666666666667, 'Chewbacca': 71.83333333333333, 'Palpatine': 71.16666666666667, 'Bib Fortuna': 70.16666666666667, 'Owen Lars': 85.83333333333333, 'Lobot': 91}
    Rank =  ['Lobot', 'Owen Lars', 'Plo Koon', 'Han Solo', 'R2-D2', 'Leia Organa', 'Chewbacca', 'Palpatine', 'Ratts Tyerell', 'Bib Fortuna']
    Passed. Please submit!


**Fin!** You've reached the end of this part. Don't forget to restart and run all cells again to make sure it's all working when run in sequence; and make sure your work passes the submission process. Good luck!
