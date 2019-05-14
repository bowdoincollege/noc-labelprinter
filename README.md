# labelprinter information

A repository for all Bowdoin College label printer information

## Templates

Please use these templates for printing consistently formatted labels.

## Database merge

For printing multiple labels for a project, it is helpful to do a database
merge.

### Create input data

Create a CSV file with one line per label.

    hubbard-server-1-e1/27;C05-G05-1 (9,10);hubbard-wlanmd-1-g0/0/4
    hubbard-server-2-e1/27;C05-G04-1 (9,10);hubbard-wlanmd-2-g0/0/4
    hubbard-dist-1-e3/29;C05-G05-9 (7,8);hubbard-wlanmd-1-g0/0/2
    hubbard-dist-1-e4/29;C05-G05-10 (7,8);hubbard-wlanmd-2-g0/0/2
    hubbard-dist-2-e3/29;C05-G04-9 (7,8);hubbard-wlanmd-1-g0/0/3
    hubbard-dist-2-e4/29;C05-G04-10 (7,8);hubbard-wlanmd-2-g0/0/3
    hubbard-wlanmd-1-g0/0/4;C05-G05-1 (9,10);hubbard-server-1-e1/27
    hubbard-wlanmd-2-g0/0/4;C05-G04-1 (9,10);hubbard-server-2-e1/27
    [...]

Note that since there is a comma in the data, it is helpful to use a semicolon
as the field delimiter.  It is best to create a separate CSV file for each type (2-, 3-, 4-line) of label, and merge those each separately.

Often, it is easy to generate these with a quick perl or python script.

### Open a template file

Open an empty 2-, 3-, or 4-line template file.

### Select the database

Select the window of the template you want to merge, and choose `File` -> `Database` -> `Connect...`.

![File>Database>Connect...](/images/file_database_connect.png?raw=true "Connect to Database")

In the "Open Database" dialog, choose the database (CSV file) you want to merge.  Deselect the "Header Row Contains Field Names", and select the "Replace Delimiter and File Encoding" options.

### Import the data

![Select File](/images/open-database_select-file.png?raw=true "Select File")

In the next dialog, select the "Semicolon" delimiter in the "Original File Conversion Delimiter" field.  Leave the "File Encoding" field at "Auto".

![Select Delimiter](/images/open-database_delimiter.png?raw=true "Select Delimiter")

In the drop-down sheet, accept (click Ok) the proposed "Line Feed Code", "Mac OS X / Unix (LF)".

![Select Encoding](/images/open-database_encoding.png?raw=true "Select Encoding")

In the "Mapping Merged Fields" dialog, select the corresponding "Database Field" for each "Layout Object" in the right-hand table.

![Map Fields](/images/open-database_map-fields.png?raw=true "Map Fields")

### Verify Records

Once the merge is complete, you can verify each record is displaying correctly by navigating the forward/back arrows (or selecting individual records) in the table displayed at the bottom of the label window.

![Verify Records](/images/verify-records.png?raw=true "Verify Records")

## Print

There is a Brother PT-9800PCN label printer, `labelprinter.mgmt.bowdoin.edu` in the lab.  Before you first print, create this device in your printing preferences.

![Define Printer](/images/printer_pt-9800pcn.png?raw=true "Define Printer")

To print to this device, first connect to the management VPN and then select `File` -> `Print`.  From the print dialog, select the "All Records" radio button under the "Database" option in the "P-touch Editor" section to print all merged records.

![Print All Reords](/images/print_all-records.png?raw=true "Print All Records")

Change to the "Cut Option" section and select the "Half Cut" option.  This will print all labels in a long string of attached labels.  This is the most efficient in terms of media waste as no leader tape needs to be used between labels.

![Select Cut Option](/images/print_cut-option.png?raw=true "Select Cut Option")

