matlab_menu_gui
===============

A powerful but simple to use graphical user interface menu in Matlab. Combines the functionality of menu (exclusive option selection) and inputdlg (text input) as well as introducing radio-button groups, check-boxes (multiple selection) and sliders (numeric selection).

Syntax:
  choice = menuN(mtitle, options)

Input:
  mtitle    - [string] - title of menu figure window
  options - [cellstr, string, double (1x2, 1x3), cell (Nx2)] - menu option type

Different types of options:
(i) Button menu (same behaviour as menu) [exclusive selection]:
  options - [cellstr] - labels for buttons, ex. 
  options = {'button1', 'button2'};
(ii) Radio-button group [exclusive selection]:
  options - [string] (first two characters 'r|') - labels for radio-group, ex.
  options = 'r|radio1|radio2';
  Start one label with '¤' sign to set it toggled on as default.
(iii) Popup-menu [exclusive selection]:
  options - [string] (first two characters 'p|') - labels for popup-menu, ex.
  options = 'p|popup1|popup2';
  Start one label with '¤' sign to set it toggled on as default.
(iv) Check-box group [multiple selection]:
  options - [string] (first two characters 'x|') - labels for check-boxes, ex.
  options = 'x|check1|check2';
  Start any label with '¤' sign to set it toggled on as default.
(v) List-box menu [multiple selection]:
  options - [string] - labels for list-box lines, ex.
  options = 'listline1|listline2';
  Start any label with '¤' sign to set it toggled on as default.
(vi) Slider [numeric value selection]:
  options - [double (1x2,1x3)] - [min, max, (initial)] slider value, ex.
  options = [0, 1];
  Add a third value (e.g. [0, 1, 0.5]) to set it as the default value.
(vii) Text box [text input]:
  options - [string] (first two characters 't|') - initial text in textbox, ex.
  options = 't|my text|with two lines';
  Add additional '|' character to allow for multiple lines in the text box.

(*) Multi-menu option with any number of the input types (ii-vii) and subtitles:
option = [cell (Nx2)] - first column any input of types (ii-vii), second column is optional [string] with subtitle for each option. ex.
options = {'p|popup1|popup2', 'Popup subtitle'; ...
                 'x|check1|check2', 'Check/box subtitle'; ...
                 [0, 1, 0.5], 'Slider subtitle'};

Output:
  choice - [double, string, cell] - selected option index, value or text
Note, if no option is selected, or the window is closed, returns -1.
If input of type (*) is used, choice is a cell array with the selected option for each individual input type.







