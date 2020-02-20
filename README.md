# Assignment: Scripting and File I/O

In this assignment, you'll practice:

* Using modules
* Reading documentation
* Scripting
* File I/O
* Using dictionaries

## Deliverables and Submitting

The usual!

---

# Part 1: TPS Report

Your boss, Bill, asks you to come in on Saturday to finish your TPS report.

You promise to finish the report, but as Bill walks away, you smile knowing you have a trick up your sleeve: scripting!

You plan on quickly writing up a bit of code to finish the report, all without spending a minute of your Saturday!

You know of a Python module called [`csv`](https://docs.python.org/3/library/csv.html) that can be used to read and write `csv` files. CSV stands for "Comma-Separated Values" and is a file type commonly used for spreadsheets.

You can check out the [`csv` docs](https://docs.python.org/3/library/csv.html) for examples of how this module works.

We'll be using [`DictWriter`](https://docs.python.org/3/library/csv.html#csv.DictWriter), which can output dictionaries to rows in a CSV file.

## `DictWriter` Example

```python
import csv

# This line opens or creates a `names.csv` file
with open('names.csv', 'w', newline='') as csvfile:

    # These are the header row values at the top
    # It should be a List!
    fieldnames = ['first_name', 'last_name']

    # This opens the `DictWriter`. Notice that we pass in the list of fieldnames
    writer = csv.DictWriter(csvfile, fieldnames)

    # Write out the header row (this only needs to be done once!)
    writer.writeheader()

    # Write as many rows as you want!
    writer.writerow({ 'first_name': 'Baked', 'last_name': 'Beans' })
    writer.writerow({ 'first_name': 'Lovely', 'last_name': 'Spam' })
    writer.writerow({ 'first_name': 'Wonderful', 'last_name': 'Spam' })
```

### Output of `DictWriter` Example

If you run the previous example, you'll end up with a `names.csv` file that looks like this when you open it in Atom:

```
first_name,last_name
Baked,Beans
Lovely,Spam
Wonderful,Spam
```

This `csv` file represents a spreadsheet that looks like this:

| first_name | last_name |
| --- | --- |
| Baked | Beans |
| Lovely | Spam |
| Wonderful | Spam |

If you double click the `names.csv` file that is generated, it will open in whatever spreadsheet program you have on your computer. On a Mac, this is probably *Numbers*. On Windows, this is probably *Microsoft Excel*. If you don't have a spreadsheet program on your computer, you can upload the file to Google Sheets and view it there.

## Your Job!

Now that you have a good idea how to wrangle a `csv` file, let's think about what you'd like to do with this newfound power.

You have a list of dictionaries called `employees`, which contains information about each employee including `first_name`, `last_name`, `hire_date`, `job_title`, and `performance_review`.

Open a new file called `tps_report.csv`, and write a loop to write out every employee in the `employees` dictionary to `tps_report.csv`.

* **Hint 1:** Think about where you can retrieve the report field names from, without having to write them all out
* **Hint 2:** Instead of writing `writer.writerow` many times (as in the example earlier), try looping through the `employees` list

### Starter Code

You can start with the starter code inside the file called `part1.py`.

### Expected Output

After you write and run your program, the `tps_report.csv` file should contain:

```
first_name,last_name,job_title,hire_date,performance_review
Bill,Lumbergh,Vice President,1985,excellent
Michael,Bolton,Programmer,1995,poor
Peter,Gibbons,Programmer,1989,poor
Samir,Nagheenanajar,Programmer,1974,fair
Milton,Waddams,Collator,1974,does he even work here?
Bob,Porter,Consultant,1999,excellent
Bob,Slydell,Consultant,1999,excellent
```

Or, if you're viewing it in a spreadsheet program, it should look something like:

| first_name | last_name | job_title | hire_date | performance_review |
| --- | --- | --- | --- | --- |
| Bill | Lumbergh | Vice President | 1985 | excellent |
| Michael | Bolton | Programmer | 1995 | poor |
| Peter | Gibbons | Programmer | 1989 | poor |
| Samir | Nagheenanajar | Programmer | 1974 | fair |
| Milton | Waddams | Collator | 1974 | does he even work here? |
| Bob | Porter | Consultant | 1999 | excellent |
| Bob | Slydell | Consultant | 1999 | excellent |

---

# (STRETCH) Part 2: Have You Seen My Stapler?

Now we have generated a TPS report... but it isn't finished. There are still a couple of things left to do!

You notice that the performance review of you and your friends are pretty bad... so let's change your performance reviews in the system. :smiling_imp:

Copy your `part1.py` file into `part2.py` file and make your changes in the new file.

1. Add a field called `review_finished` to each employee. The value for every row should be `yes`.
   * **Hint 1**: You figure you can just add this field to each dictionary inside the loop
   * **Hint 2**: Don't forget to update the headers in the report!
1. Change everyone's `performance_review` to `excellent`... Unless it's your boss Bill Lumbergh or someone with the `job_title` of `Consultant`. In that case, make their `performance_review` value `poor`. (Hehehe)
1. Re-generate the TPS Report and make sure your new program does the job.
1. Enjoy the rest of your (fictional) Saturday!

**Hint**: Don't forget that you can always write a function if your code starts getting too long!

---

# Look at You, Being a Boss!

What do you call a snake that's 3.14 meters long?

![](https://media.giphy.com/media/3owyoUHuSSqDMEzVRu/giphy.gif)

A `Pi-Thon`! :grin:
