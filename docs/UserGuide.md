---
  layout: default.md
  title: "User Guide"
  pageNav: 3
---

# TutorsContactsPro User Guide

TutorsContactsPro is a **desktop app for tutors teaching Computer Science courses to manage their students, optimized for use via a  Line Interface** (CLI) while still having the benefits of a Graphical User Interface (GUI). If you can type fast, TutorsContactsPro can help you to gain faster and more convenient access to your list of students, even if they are from different classes.

<!-- * Table of Contents -->
<page-nav-print />

## Quick Overview

* [Quick start ](#feature-start)

* [Features ](#feature-features)

  * [Viewing help: `help` ](#feature-help)

  * [Listing all students: `list` ](#feature-list)

  * [Adding a student: `add`](#feature-add)

  * [Editing a student: `edit`](#feature-edit)

  * [Locating students using keyword: `find`](#feature-find)

  * [Filtering students using group: `filter`](#feature-filter)

  * [Deleting a student: `delete`](#feature-delete)

  * [Clearing all entries: `clear`](#feature-clear)

  * [Exiting the program: `exit` ](#feature-exit)

* [FAQ](#feature-faq)

* [Known issues](#feature-issues)

* [Command Summary](#feature-summary)

--------------------------------------------------------------------------------------------------------------------

## <span id='feature-start'> Quick start <span>

> [!important]
> 1. Ensure you have Java `11` or above installed in your Computer.

[//]: # (<box type="info" seamless>)

2. Download the latest `addressbook.jar` from [here](https://github.com/se-edu/addressbook-level3/releases).

3. Copy the file to the folder you want to use as the _home folder_ for your AddressBook.

4. Open a command terminal, `cd` into the folder you put the jar file in, and use the `java -jar addressbook.jar` command to run the application.<br>
   A GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/UpdatedUi.png)

4. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:

   * `list` : Lists all students.

   * `add n/John Doe p/98765432 e/johnd@example.com y/2 m/Computer Science tg/johndoe r/Very quiet student g/TUT04 g/LAB10 ` : Adds a student named `John Doe` to the list.
   
   * `edit 1 p/93840823 y/3 tg/jiejfh203` : Edits the first student on the current list. 
   
   * `find John Tan` : Lists all the students with names that matches 'John' or 'Tan'.

   * `filter TUT10` : Lists all the students in group 'TUT10'

   * `delete 3` : Deletes the 3rd student shown in the current list.

   * `clear` : Deletes all students on the list.

   * `exit` : Exits the app.


5. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## <span id='feature-features'> Features <span>

[//]: # (<box type="info" seamless>)

**Notes about the command format:**<br>

| Command format        | Representation                                                                                                                  | Examples                                                                                      |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `UPPER_CASE`          | Words in `UPPER_CASE` are the parameters to be supplied by the user                                                             | in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`                  |
| square brackets `[]`  | Items in square brackets are optional                                                                                           | `n/NAME [g/Group]` can be used as `n/John Doe g/TUT` or as `n/John Doe`                      |
| `…`                   | Items with `…`​ after them can be used multiple times including zero times                                                      | `[g/GROUP]…​` can be used as `g/TUT03`, `g/LAB01`, `g/REC08` etc            |
| Order                 | Parameters can be in any order                                                                                                  | if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable. |
| Extraneous parameters |  Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit` and `clear`) will be ignored | if the command specifies `help 123`, it will be interpreted as `help`                         |                                                                                                 | Singapore phone number, 8 digits, without country code                                        |

> [!Note]
> If you are using a PDF version of this document, be careful when copying and pasting commands that span multiple lines as space characters surrounding line-breaks may be omitted when copied over to the application.

### <span id='feature-help'> Viewing help : `help` </span>

Allows you to easily access tge features in TutorsContactsPro

![help message](images/helpMessage.png)

Format: `help`

### <span id='feature-list'> Listing all students : `list` </span>

Shows a list of all your students.

Format: `list`

**Tip:** Auto-capitalization will be handled. Extra/trailing/leading spaces will be removed



### <span id='feature-add'> Adding a student: `add` </span>

You can add a student to the list.

Format: `add n/NAME p/PHONE_NUMBER e/EMAIL y/YEAR m/MAJOR tg/TELEGRAM_HANDLE [r/REMARK] [g/Group]...`


| Parameter         | Representation                        | Constraints                                                                        |
|-------------------|---------------------------------------|------------------------------------------------------------------------------------|
| `NAME`            | Name of the student                   | Auto-capitalization will be handled. Extra/trailing/leading spaces will be removed |
| `PHONE_NUMBER`    | Phone number of the student           | Singapore phone number, 8 digits, without country code                             |
| `EMAIL`           | Email of the student                  | Must be in email format `username`@`email`.com                                     |
| `YEAR`            | Academic Year of the student          | A number ranging from 1 - 6, inclusive                                             |
| `MAJOR`           | Academic Major of the student contact | String to represent the major                                                      |
| `TELEGRAM_HANDLE` | Telegram handle of the student        | Telegram handle format (a-z, 0-9 and underscores, case-insensitive), without prefix “@” |
| `REMARKS`         | Additional remarks of the student     | A case-sensitive string. This can be anything                                      |
| `GROUP`           | Tutorial/Lab/Recitation slot          | Must be in correct slot format TUT/LAB/REC`2-digit number`                         |

Examples:
* `add n/John Doe p/98765432 e/johnd@example.com y/2 m/Computer Science tg/johndoe r/Very quiet student g/TUT04 g/LAB10 `
* `add n/Kendra Huetta p/98765367 e/Kendra@example.com y/1 m/Computer Science tg/KendraHuetta r/quiet student g/LAB10 `
  ![result for 'add Kendra Huetta'](images/addFeature.png)

### <span id='feature-edit'> Editing a student : `edit` <span>

Edits an existing student you have selected.

Format: `edit INDEX [n/NAME] [p/PHONE_NUMBER] [e/EMAIL] [y/YEAR] [m/MAJOR] [tg/TELEGRAM_HANDLE] [r/REMARK] [g/Group]`

* Edits the student at the specified `INDEX`. The index refers to the index number shown in the displayed student list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing groups, the existing groups of the student will be removed i.e adding of groups is not cumulative.
* You can remove all the student’s groups by typing `g/` without specifying any groups after it.
* You can remove the remark of a student by typing `r/` without specifying any groups after it. 

Examples:
*  `edit 1 n/John e/john01@example.com` Edits the name of the first student to `John` and email to `john01@example.com` respectively.
*  `edit 2 n/Betty tg/` Edits the name of the 2nd student to be `Betty` and clears her telegram handle.

### <span id='feature-find'> Locating students by keyword: `find` <span>

Finds students whose details contain any of the given keywords.
You can find the student even if the keywords **matches partially**. 

Format: `find KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only the student's name is searched.
* Students matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find John` returns `john` and `John Doe`
* `find Jo` returns `John Doe`, `Johan Louis`<br>
  ![result for 'find Jo'](images/findFeature.png)

### <span id='feature-filter'> Filtering students using group: `filter` <span>

Filters and list students belonging to any of the given group name keyword.
You can filter students when the keywords **matches fully**.

Format: `filter KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only student's group name is searched.
* Students matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `filter TUT04 ` returns `John Doe` and `Johan Louis` belonging to the tutorial group `TUT04`
  ![result for 'filter TU'](images/filterFeature.png)


### <span id='feature-delete'> Deleting a student : `delete` <span>

Deletes your specified student from the current list.

Format: `delete INDEX`

* Deletes the student at the specified `INDEX`.
* The index refers to the index number shown in the current displayed student list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `delete 2` deletes the 2nd student in the major book.
* `find Betsy` followed by `delete 1` deletes the 1st student in the results of the `find` command.

### <span id='feature-clear'> Clearing all entries : `clear` <span>

Clears all student entries from TutorsContactsPro.

Format: `clear`

### <span id='feature-exit'> Exiting the program : `exit` <span>

Exits the program.

Format: `exit`

### Saving the data

TutorsContactsPro data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Editing the data file

TutorsContactsPro data are saved automatically as a JSON file `[JAR file location]/data/TutorsContactsPro.json`. Advanced users are welcome to update data directly by editing that data file.

[//]: # (<box type="warning" seamless>)

> [**Caution:**]
If your changes to the data file makes its format invalid, TutorsContactsPro will discard all data and start with an empty data file at the next run.  Hence, it is recommended to take a backup of the file before editing it.<br>
Furthermore, certain edits can cause the TutorsContactsPro to behave in unexpected ways (e.g., if a value entered is outside the acceptable range). Therefore, edit the data file only if you are confident that you can update it correctly.
</box>

### Archiving data files `[coming in v2.0]`

_Details coming soon ..._

--------------------------------------------------------------------------------------------------------------------

## <span id='feature-faq'> FAQ <span>

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous TutorsContactsPro home folder.

--------------------------------------------------------------------------------------------------------------------

## <span id='feature-issues'> Known issues <span>

1. **When using multiple screens**, if you move the application to a secondary screen, and later switch to using only the primary screen, the GUI will open off-screen. The remedy is to delete the `preferences.json` file created by the application before running the application again.

--------------------------------------------------------------------------------------------------------------------

## <span id='feature-summary'> Command summary <span>

| Action     | Format, Examples                                                                                                                                                                                                   |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Help**   | `help`                                                                                                                                                                                                             |
| **List**   | `list`                                                                                                                                                                                                             |
| **Add**    | `add n/NAME p/PHONE e/EMAIL y/YEAR m/MAJOR tg/TELEGRAM [r/REMARK] [g/Group]...` <br> e.g., `add n/John Doe p/98765432 e/johnd@example.com y/2 m/Computer Science tg/johndoe r/Very quiet student g/TUT04 g/LAB10 ` |
| **Edit**   | `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [y/NUMBER] [m/MAJOR] [tg/TELEGRAM] [r/REMARK] [g/Group]`<br> e.g., `edit 1 n/John e/john01@example.com`                                                                   |
| **Find**   | `find KEYWORD [MORE_KEYWORDS]`<br> e.g.,`find john tan`                                                                                                                                                            |
| **Filter** | `filter KEYWORD [MORE_KEYWORDS]`<br> e.g.,`filter TUT01`                                                                                                                                                           |
| **Delete** | `delete INDEX`<br> e.g., `delete 1`                                                                                                                                                                                |  
| **Clear**  | `clear`                                                                                                                                                                                                            |
