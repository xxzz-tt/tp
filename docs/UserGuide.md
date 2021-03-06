---
layout: page
title: User Guide
---


Recretary is a **desktop app for managing contacts and meetings, optimized for use via a Command Line Interface** (CLI) while still having the benefits of a Graphical User Interface (GUI). If you can type fast, Recretary can get your contact management tasks done faster than traditional GUI apps.

* First Run
* Features
    * Contact & Meeting Management
        * Adding a person/ meeting : `add <contact | meeting>`
        * Listing all persons/ meetings: `list <contact | meeting>` 
        * Editing a person/ meeting: `edit <contact | meeting>` 
        * Locating persons/ meetings: `find <contact | meeting>` 
        * Deleting a person/ meeting: `delete <contact | meeting>`
    * General
        * Clearing all entries : `clear`
        * Viewing help : `help`
        * Exiting the program : `exit`
        * FAQ
    * Command summary
  
    

--------------------------------------------------------------------------------------------------------------------

## Quick start

1. Ensure you have Java `11` or above installed in your Computer.

1. Download the latest `addressbook.jar` from [here](https://github.com/se-edu/addressbook-level3/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your AddressBook.

1. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

1. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:

   * **`list`** : Lists all contacts.

   * **`add`**`n/John Doe p/98765432 e/johnd@example.com a/John street, block 123, #01-01` : Adds a contact named `John Doe` to the Address Book.

   * **`delete`**`3` : Deletes the 3rd contact shown in the current list.

   * **`clear`** : Deletes all contacts.

   * **`exit`** : Exits the app.

1. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

</div>

### Viewing help : `help`

Shows a message explaning how to access the help page.

![help message](images/helpMessage.png)

Format: `help`

### Contact & Meeting management
#### Adding a person: `add`

Adds a person or meeting to the address book.

Format: `add <contact | meeting>`

Adds a person to the address book.
 
Format: `add contact n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS c/COMPANY [r/COMPANY_ROLE] [t/TAG]…​`

<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
A person can have any number of tags (including 0)
</div>

Examples:
* `add contact n/John Doe p/98765432 e/johnd@example.com a/John street, block 123, #01-01 c/ABC Holdings Pte. Ltd`
* `add contact n/Betsy Crowe t/friend e/betsycrowe@example.com a/Newgate Mansion p/1234567 r/CEO c/DEF Company`

Adds a meeting into the meeting schedule 
 
Format: `add meeting d/DATETIME dur/DURATION t/TITLE [l/LOCATION]`

Add participants into the meeting with this format:  
E.g.  
`Recretary: Enter the next participant’s name, or type end/ to finish inputting participants.`  
`User: john doe`  
`Recretary: Here is a list of your contacts that match ‘john doe’`  
<code> &nbsp; 1. John doe, abc company </code>  
<code> &nbsp; 2. John doe, def company </code>  
`User: 2`  
`Recretary: added John doe, def company to participants list.`  
`Enter the next participant’s name, or type end/ to finish inputting participants.`  
`User: end/`

<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
Only people in your contacts can be added as participants.
</div>

Examples:
* add meeting d/2020-12-31 14:00 dur/60 t/abc company meeting l/John street, block 123, #01-01

### Listing all persons : `list`

Format: `list <contact | meeting>`

Shows a list of all persons in the address book.

Format: `list contact`
 
Shows a list of all meetings in the address book.

Format: `list meeting`


### Editing an item : `edit`

Edits an existing person in the address book.

Format: `edit <contact | meeting>

Edits an existing person in the address book.
 
Format: `edit contact INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [c/COMPANY] [t/TAG] [r/COMPANY_ROLE]…`

* Edits the person at the specified `INDEX`. The index refers to the index number 
shown in the displayed person list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the person will be removed i.e adding of tags is not cumulative.
* You can remove all the person’s tags by typing `t/` without
    specifying any tags after it.

Examples:
*  `edit contact 1 p/91234567 e/johndoe@example.com` Edits the phone number and email address of the 1st person to be 
`91234567` and `johndoe@example.com` respectively.
*  `edit 2 n/Betsy Crower t/` Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.

Edits an existing meeting in the meeting schedule.
 
Format: `edit meeting INDEX [d/DATETIME] [t/TITLE] [l/LOCATION] [p/]...`

Edit participants in a meeting with this format:  
E.g.   
`Recretary: Here is the current list of participants.`  
<code> &nbsp; 1. John doe, abc company </code>  
<code> &nbsp; 2. John doe, def company </code>  
`Enter the next participant’s index to delete, or type end/ to finish removing participants.`  
`User: 1`  
`Recretary: Here is the current list of participants.`  
<code> &nbsp; 1. John doe, def company </code>  
`Enter the next participant’s index to delete, or type end/ to finish removing participants.`  
`User: end/`  

* Edits the meeting at the specified `INDEX`. The index refers to the index number shown in the displayed meeting list. 
The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.

Examples:
 
* `edit meeting 1 d/10-11-2020 14:00 l/clementi` Edits the datetime and location of the 1st meeting to be 
`10/11/2020 1400` and `clementi` respectively.

### Locating persons by name: `find`

Finds persons whose names contain any of the given keywords.

Format: `find <contact | meeting>`

Find contacts/ meetings whose names contain any of the given keywords.
 
Format: `find meeting KEYWORD [MORE_KEYWORDS]` or
`find contact KEYWORD [MORE_KEYWORDS]`


* The search is case-insensitive. e.g `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only the name is searched.
* Only full words will be matched e.g. `Han` will not match `Hans`
* Persons matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find contact John` returns `john chan` and `John Doe`
* `find meeting abc def` returns `abc meeting`, `def meeting`<br>
  ![result for 'find alex david'](images/findAlexDavidResult.png)

### Deleting a person : `delete`

Deletes the specified person from the address book.

Format: `delete <contact | meeting> <INDEX | all>

Format: `delete <contact | meeting> all`
 
Clears all entries from the address book/meeting schedule.

Format: `delete <contact | meeting> INDEX`

Deletes the specified person from the address book. 
 
Format: delete contact INDEX
`
* Deletes the person at the specified `INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `delete contact 2` deletes the 2nd contact in the address book.
* `find contact Betsy` followed by `delete contact 1` deletes the 1st contact in the results of the `find` command.

Format: `delete meeting INDEX`
 
Deletes the meeting at the specified `INDEX`.
* The index refers to the index number shown in the displayed meeting list.
* The index **must be a positive integer** 1, 2, 3, …​  

Examples:
* Use `list meeting` to check the index of the meeting to be deleted, followed by `delete meeting 2` to delete the 2nd meeting in the address book.


### Clearing all entries : `clear`

Clears all entries from the address book.

Format: `clear`

### Exiting the program : `exit`

Exits the program.

Format: `exit`

### Saving the data

AddressBook data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Archiving data files `[coming in v2.0]`

_{explain the feature here}_

--------------------------------------------------------------------------------------------------------------------

## FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous AddressBook home folder.

--------------------------------------------------------------------------------------------------------------------

## Command summary

Action | Format, Examples
--------|------------------
**Add** | `add contact n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS c/COMPANY [r/COMPANY_ROLE] [t/TAG]…` <br> e.g., `add contact n/James Ho p/22224444 e/jamesho@example.com a/123, Clementi Rd a/XYZ Company r/manager t/friend t/colleague` <br> `add meeting d/DATETIME dur/DURATION t/TITLE [l/LOCATION]` <br> e.g., `add meeting d/2020-12-31 14:00 dur/60 t/abc company meeting l/John street, block 123, #01-01`
**Clear** | `clear`
**Delete** | `delete contact INDEX`<br> e.g., `delete contact 3` <br> `delete meeting INDEX`<br> e.g., `delete meeting 5`
**Edit** | `edit contact INDEX [n/NAME] [p/PHONE_NUMBER] [e/EMAIL] [a/ADDRESS] [c/COMPANY] [r/COMPANY_ROLE] [t/TAG]…`<br> e.g.,`edit contact 2 n/James Lee e/jameslee@example.com` <br> `edit meeting INDEX [d/DATETIME] [dur/DURATION] [t/TITLE] [l/LOCATION]`<br> e.g.,`edit contact 1 dur/90 l/COM2 LT17`
**Find** | `find contact KEYWORD [MORE_KEYWORDS]`<br> e.g., `find contact James Jake` <br> `find meeting KEYWORD [MORE_KEYWORDS]`<br> e.g., `find meeting recretary stakeholders`
**List** | `list contact` <br> `list meeting`
**Help** | `help`
