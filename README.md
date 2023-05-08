Download Link: https://assignmentchef.com/product/solved-seng265-python_assignment4
<br>
The formatting and layout instructions can often require several layers of bulky HTML​​ language, which is used to describe the layout and content of web pages, has a famously verbose syntax: relatively simpleHTML​​  tags. Modern HTML​​                                                                                                is very flexible for specifying

visual aspects of the displayed content. However, extracting information from the HTML​​   representation can be difficult. The goal of this assignment is to write a Python 3 table_to_csv.py​​         program which converts HTML​​  tables to a CSV​​               representation.

The following sections describe input                       HTML​​                          Tables, a Specification​​   Implementation advice​​ for the program you are expected to write as well as an example<sub>. We also provide a </sub>Testing​​ <sub> component</sub> <sub> </sub>

HTML​​      <sub> and expected </sub>CSV​​        <sub> representation, along with some </sub>and a set of testing files. We close out with a section describing What you should Submit​​              and the Evaluation​​        scheme is also provided. Your code is expected to run ​<strong>without warnings in the course lab</strong>​ using Python version 3.




<h2>HTML Tables</h2>

Tables in at ​<a href="https://www.w3schools.com/html/html_tables.asp">http://www.w3schools.com/html/html_tables.as</a>HTML​​   are specified with the &lt;​ table&gt;​ tag. A brief tutorial on the <a href="https://www.w3schools.com/html/html_tables.asp">p</a><u>​</u><a href="https://www.w3schools.com/html/html_tables.asp">.</a> Note that whitespace in &lt;​ table​HTML​​            <sub> is generally ignored: spaces, newlines and tabs are</sub>&gt; tag, along with interactive examples, can be found  collapsed into a single space when the page is rendered. Line breaks are specified by the &lt;​ br /&gt;​ tag. Consider the HTML​​ table below (which appears as the first example in the tutorial linked above).




&lt;table style=”width:100%”&gt;

&lt;tr&gt;

&lt;th&gt;Company&lt;/th&gt;

&lt;th&gt;Contact&lt;/th&gt;

&lt;th&gt;Country&lt;/th&gt;

&lt;/tr&gt;

&lt;tr&gt;

&lt;td&gt;​Alfreds Futterkiste​&lt;/td&gt;

&lt;td&gt;​Maria Anders​&lt;/td&gt;

&lt;td&gt;​Germany​&lt;/td&gt;

&lt;/tr&gt;

&lt;tr&gt;

&lt;td&gt;​Centro comercial Moctezuma​&lt;/td&gt;

&lt;td&gt;​Francisco Chang​&lt;/td&gt;

&lt;td&gt;​Mexico​&lt;/td&gt;

&lt;/tr&gt;

&lt;/table&gt;




The table described by the HTML code above would be rendered by a web browser in a similar format to the table below.

<table width="387">

 <tbody>

  <tr>

   <td width="128"><strong>Company</strong></td>

   <td width="138"><strong>Contact</strong></td>

   <td width="121"><strong>Country</strong></td>

  </tr>

  <tr>

   <td width="128">AlfredsFutterkiste</td>

   <td width="138">Maria Anders</td>

   <td width="121">Germany</td>

  </tr>

  <tr>

   <td width="128">Centro comercial Moctezuma</td>

   <td width="138">Francisco Chang</td>

   <td width="121">Mexico</td>

  </tr>

 </tbody>

</table>




The The &lt;​&lt;​ tr&gt;​th&gt;​ and  and &lt;​&lt;​ /tr&gt;​/th&gt;​ tags enclose the data for each row of the table, and the  tags enclose the contents of header cells, but their use is optional (some authors use regular &lt;​ td&gt;​ and ​&lt; /td&gt;​ tags enclose the contents of each cell.&lt;​ td&gt;​ tags for        header cells). Cells of a table may contain HTML​​       code, including other HTML​​    tables.

Tag names are not case sensitive, so `&lt;​ tD&gt;​’ and `&lt;​ TD&gt;​’ are both valid forms of the `&lt;​ td&gt;​’ tag. Any HTML​​              tag may contain attributes that change its appearance.

The most common attribute in modern HTML​​               is `style’​​             &lt;​. For example, make the contents of a particular cell boldfaced, the attributetd&gt;​<sub> tag:          </sub> style=”font-weight: bold;​<sub>” can be added to the </sub>

&lt;td style=”font-weight: bold;”&gt;​Alfreds Futterkiste​&lt;/td&gt;

Additionally, any Whitespace is not permitted between the opening `HTML​​ tag may contain whitespace after the tag name, between attributes or before the closing `&lt;​ ​’ character and the tag name. For example, `&lt;​ td &gt;​’ and `&lt;​ /td &gt;​&gt;​ ​’ character.’ are valid tags,  but `&lt;​ /td&gt;​’ and `&lt;​ td &gt;​’ are not.

Since whitespace in HTML​​      is generally ignored, there is no requirement that the table be laid out in a readable way in the HTML​​      code. The table in the example above could also be represented by the code below.

&lt;table style=”width:100%”&gt; &lt;tr &gt; &lt;th &gt;Company&lt;/th &gt;&lt;th&gt; Contact&lt;/th&gt;&lt;th&gt;Country&lt;/th&gt;&lt;/tr

&gt;&lt;tr&gt;&lt;td&gt;​Alfreds Futterkiste​&lt;/td&gt;

&lt;td&gt;​Maria Anders​&lt;/td&gt;&lt;td &gt;​Germany​&lt;/td&gt;

&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;​Centro comercial Moctezuma​&lt;/td&gt;&lt;td&gt;​Francisco Chang​&lt;/td&gt; &lt;td&gt;​Mexico​&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;

This assignment assumes the following extra constraints to any basic HTML​​      table specification used as test input file.

<ul>

 <li>To be considered valid, a test input must be valid in turn must be inside a &lt;​ table&gt;​ All opening tags must have a matching closing tag (note that some HTML​​ . For example, tags like &lt;​ td&gt;​ can only occur inside of a HTML​​     <sub> tags, like </sub>&lt;​ tr&gt;​ tag, which​&lt; br</li>

</ul>

/&gt;​, are singular and do not need a closing tag), and vice versa.

<ul>

 <li>Between the opening angle bracket (&lt;​ ​) and closing angle bracket (&gt;​ ​) of a tag, no other instances of closing angle brackets are permitted (including inside of attributes).</li>

 <li>Commas may not appear inside the data for a cell. However, other aspects of the HTML which are not cell content (such as the style attributes of &lt;​ td&gt;​ tags) may contain commas.</li>

 <li>Cells may contain any data, including other HTML​​ tags, but may not contain nested &lt;​ table&gt;​ The prohibition on comma use applies to all contents of each cell, including HTML​​ tags. <strong>In other words, if the comma character appears between the</strong>​        <strong> opening </strong><strong>&lt;</strong>​ <strong>td&gt;​ tag and its matching </strong><strong>&lt;</strong>​ <strong>/td&gt;​ tag, the input will be considered invalid. </strong>●    There is no requirement that each row of the table contain the same number of columns.</li>

 <li>Every HTML​​ table must have at least one row.</li>

 <li>Every row of an HTML​​ table must contain at least one cell.</li>

 <li>The rowspan​​ and colspan​​      , which are used to make cells span multiple rows or columns, are not permitted.</li>

</ul>




<h2>HTML-to-CSV Converter</h2>

Your task is to write a Python 3 program called representation of each table in the input, including any header cells specified with table_to_csv.py​​         which reads HTML​​ &lt;​ th&gt;​ from standard input and outputs a <sub> (if present).                                                                                                                                                         </sub>CSV​

The resulting CSV​​   data will be printed to standard output in the following format:

TABLE 1:

&lt;CSV data for first table in the input&gt;




TABLE 2:

&lt;CSV data for the second table in the input&gt;




TABLE 3:

&lt;CSV data for the third table in the input&gt;

…

Your implementation may assume that the input table complies with the constraints given in the previous section, and must also meet the following requirements.

<ul>

 <li>All runs of one or more spaces, newlines, tabs, or other whitespace should be collapsed into a single space.</li>

 <li>Within a table cell, all HTML tags are to be left intact.</li>

 <li>The contents of each table cell should be stripped of all leading and trailing whitespace before being output. For example, the cell `&lt;​ td&gt; Lemon Meringue &lt;/td&gt;​’ should be output as `Lemon Meringue’ (note that the multiple spaces between the two words are also collapsed into one space).</li>

 <li>Every row of the output CSV​​ spreadsheet must contain the same number of columns (recall that the number of columns in a row of a CSV​​ spreadsheet is the number of commas in the row minus one). If the rows of the HTML​​   table contain a differing number of columns, then the number of columns in the output spreadsheet should be equal to the number of columns in the row of the input table with the largest number of columns. Other rows should be padded with blank cells to meet the column requirement.</li>

</ul>




As an example, consider the following input HTML​​  table below:




&lt;table&gt;&lt;tr&gt;

&lt;th&gt;Student Number&lt;/th&gt;&lt;th&gt;Student Name&lt;/th&gt;&lt;th&gt;Major&lt;/th&gt;

&lt;th&gt;A1 mark&lt;/th&gt;&lt;th&gt;A2 mark&lt;/th&gt;&lt;/tr &gt;

&lt;tr&gt;&lt;td&gt;V00000001&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;10&lt;/td&gt;

&lt;td&gt;11&lt;/td&gt;

&lt;/tr&gt;

&lt;tr&gt;&lt;td&gt;V00123456&lt;/td&gt;&lt;td&gt;Alastair Avocado&lt;/td&gt;

&lt;td&gt;Psychology&lt;/td&gt;&lt;td&gt;12&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;

&lt;tr &gt;

&lt;td&gt;V00123457&lt;/td &gt;

&lt;td&gt;Rebecca Raspberry

&lt;/td&gt;&lt;td&gt;Computer Science&lt;/td&gt;&lt;td&gt;17&lt;/td&gt;&lt;td&gt;14&lt;/td&gt;&lt;/tr&gt;

&lt;tr&gt;&lt;td&gt;V00314159&lt;/td&gt;&lt;td&gt;Fiona Framboise&lt;/td&gt;

&lt;td style=”font-family: monospace; font-size: 20pt; font-weight: bold;”&gt;

Computer Science




&lt;/td&gt;

&lt;td&gt; &lt;/td&gt;&lt;td&gt;17&lt;/td&gt;&lt;/tr&gt;

&lt;tr&gt;&lt;td&gt;V00654321&lt;/td&gt;&lt;td&gt;Meredith Malina&lt;/td&gt;

&lt;td style=”color: red;”&gt;Software Engineering&lt;/td&gt;&lt;td&gt;18&lt;/td&gt;&lt;td&gt;12&lt;/td&gt;&lt;/tr&gt;

&lt;tr&gt;&lt;td&gt;V00654322&lt;/td&gt;&lt;td&gt;Hannah Hindbaer&lt;/td&gt;&lt;td&gt;Physics&lt;/td&gt;&lt;td&gt;15&lt;/td&gt;&lt;td&gt;18&lt;/td&gt;&lt;/tr&gt;

&lt;tr&gt;&lt;td&gt;V00951413&lt;/td&gt;&lt;td&gt;Neal Naranja&lt;/td&gt;&lt;td&gt;Anthropology&lt;/td&gt;&lt;td&gt;15&lt;/td&gt;&lt;td&gt;15&lt;/td&gt;&lt;/tr&gt;

&lt;/table&gt;




When provided as input to a correct HTML-to-CSV​​      implementation, the HTML​​       table above would be converted to the following CSV​               representation.




TABLE 1:

Student Number,Student Name,Major,A1 mark,A2 mark

V00000001,,,10,11

V00123456,Alastair Avocado,Psychology,12,

V00123457,Rebecca Raspberry,Computer Science,17,14

V00314159,Fiona Framboise,Computer Science,,17

V00654321,Meredith Malina,Software Engineering,18,12

V00654322,Hannah Hindbaer,Physics,15,18

V00951413,Neal Naranja,Anthropology,15,15







<h2>Implementation Advice</h2>

Since HTML​​     allows such a wide variation in the structure and formatting of tags, the use of regular expressions to match each tag pair is encouraged. However, you are not required to use regular expressions (or any other particular implementation technique, as long as your code is valid Python 3). If you use regular expressions, be aware of the following points.

<ul>

 <li>By default, the `line boundary, it will not match. For example, the pattern `.​​ ‘ specifier does not match the newline character (`A.*B​​ <sub>‘ would match `</sub>
​​ ‘), so if you are searching for something which crosses aAxy z B​​ <sub>‘ but not `</sub>Axy
 z B​​                         <sub>‘ by default. Since</sub> <sub> </sub></li>

</ul>

whitespace in HTML​​     can be collapsed to a single space, you can remedy this problem by replacing all newlines characters with spaces. You can also use the `re.DOTALL​​           ‘ flag when performing regular expression matching, which will cause newlines to be matched by the `.’ specifier. Consider the interactive Python 3 session below, which contains examples of both methods.




&gt;&gt;&gt; s1 = ‘Axy z B’

&gt;&gt;&gt; s2 = ‘Axy
 z B’

&gt;&gt;&gt; re.match(‘A.*B’,s1)

&lt;_sre.SRE_Match object; span=(0, 8), match=’Axy z B’&gt;

&gt;&gt;&gt; re.match(‘A.*B’,s2)

&gt;&gt;&gt; re.findall(‘A.*B’,s1)

[‘Axy z B’]

&gt;&gt;&gt; re.findall(‘A(.*)B’,s1) [‘xy z ‘]

&gt;&gt;&gt; re.findall(‘A(.*)B’,s2)

[]

&gt;&gt;&gt; re.findall(‘A(.*)B’,s2, re.DOTALL)

[‘xy
 z ‘]

&gt;&gt;&gt; s3 = s2.replace(‘
’,’ ‘)

&gt;&gt;&gt; s3

‘Axy z B’

&gt;&gt;&gt; re.findall(‘A(.*)B’,s3)

[‘xy z ‘]




<ul>

 <li>Since HTML​​ tag names are not case sensitive, you may want to use the `re.IGNORECASE’​​            flag to enable case-insensitive matching. Consider the interactive session below.</li>

</ul>

&gt;&gt;&gt; x = ‘abc’

&gt;&gt;&gt; y = ‘Abc’

&gt;&gt;&gt; z = ‘A——C’

&gt;&gt;&gt; re.findall(‘a.*c’,x) [‘abc’]

&gt;&gt;&gt; re.findall(‘a.*c’,y) []

&gt;&gt;&gt; re.findall(‘a.*c’,z)

[]

&gt;&gt;&gt; re.findall(‘a.*c’,y,re.IGNORECASE) [‘Abc’]

&gt;&gt;&gt; re.findall(‘a.*c’,z,re.IGNORECASE)

[‘A——C’]




Note that if you want to use multiple ags (such as both `OR​​                operator (for example,           re.DOTALL​​              ‘ and `re.IGNORECASE​​  ‘), you can combine them with the bitwise-

`re.findall(‘a.*c’,z, re.IGNORECASE|re.DOTALL)’)​<sub>. </sub>




<h2>Constraints</h2>

You may only use use python3​​            modules that are installed on the lab computers. If a python3​​            module is not installed, you may not use that module in your code.




<h2>Test Inputs</h2>

You should ensure that your program appropriately handles error cases (such as files which do not exist – you “know the drill” from all the previous assignments) and does not produce errors on valid inputs. Since thorough testing is an integral part of the software engineering process, your git repo​​ also provides a test folder which contains 3 sub-folders each containing an ​ HTML test input​ file​ (containing various HTML​​ tables) used to evaluate assignment 4, together with the expected output csv​​ representation (output.txt​​ ). The test input files​​ must be read from stdin​​ , as in the following example usage pattern: python3 table_to_csv.py &lt; input.html &gt; your_output.txt

The test the expected output (i.e. ​suite and correctness checker will be run exactly as in previous assignments — the output you generate should strive to matchdiff your_out1.txt out1.txt​​  <sub>), and you can use the same techniques you’ve established for ensuring </sub>

quality and correctness.