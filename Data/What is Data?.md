
>[!INFO] 
>In simplest terms, data is just a record of an observation in a system

A temperature reading, a sale that happened, a customer's name, a click on a button, anything that happened or exists, written down in a form you can store and refer back to is Data.

Examples of data could be of noting down heights of students in a class.
Here are some arbitrary heights of students: Student1: 150 cm, Student2: 145 cm, Student3: 163 cm, Student4: 158 cm, Student5: 147 cm

If we were to arrange the recorded observations into a tabular format, the data becomes easier to read, understand and modify.

| Students | Heights |
| -------- | ------- |
| Student1 | 150 cm  |
| Student2 | 145 cm  |
| Student3 | 163 cm  |
| Student4 | 158 cm  |
| Student5 | 147 cm  |

Now, with the heights recorded, if I want to also record the weights of the students, say we again take random weights for the students: Student1: 52kg, Student2: 48kg, Student3: 59kg, Student4: 55kg, Student5: 52kg.

I could add these weights to the above table by just adding a new `weights` column.

| Students | Heights | Weights |
| -------- | ------- | ------- |
| Student1 | 150 cm  | 52 Kg   |
| Student2 | 145 cm  | 48 Kg   |
| Student3 | 163 cm  | 59 Kg   |
| Student4 | 158 cm  | 55 Kg   |
| Student5 | 147 cm  | 52 Kg   |

Notice how the data is arranged. While I can get a whole view of heights and weights of the students, each row in this table contains data about a particular student. This is basically a 2-dimensional data structure with the capability to slice into the required sections we require. 

If I slice over a row of the data, for example let's take Student1.
Here is how their data would look like.

| Students | Heights | Weights |
| -------- | ------- | ------- |
| Student1 | 150 cm  | 52 Kg   |
What you see here is that the height and weight of the particular student, In other words, the columns height and weight are connected to a particular student which forms a relation between the key (The Student) and the rest of the attributes (Height and Weight). This arrangement of different data points is called the Relational Data. The whole table is called a ***Relation***
