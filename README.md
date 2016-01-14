menuN - Improved menu for Matlab
===============

A powerful but simple to use graphical user interface menu in Matlab. Creates an automatically sized gui menu at the center of the screen with the supplied figure title and waits for user input. 
7 different types of menu styles are available: Push-button *, Radio-button *, Popup-menu/list *, Check box ^, List box ^, Slider and Text box. The styles marked by * represent exlusive selection, i.e. only one option can be selected. The syles marked by ^ represent multiple selection, i.e. none to all options can be selected. The slider style creates a slider which returns a numeric value in given range. The text box style returns the written text or numeric input that the user specifies in the edit/text box field. 
A default selection/value/text is also possible to specify when applicable. 

In addition to the different menu styles, multiple groups of options can be presented in the same menu to quickly create a small application specific user interface. This feature can also display subtitles for each option group. 

The syntax and usage of menuN is similar to the Matlab function menu. However, some additional formats of the inputs and output have been added to make use of the additional features.   

Syntax:

	choice = menuN(mtitle, options)
  
	mtitle	- [string] - Title of menu window
	options	- [various] - Menu options
	
Style specific input options with examples:

	Push-buttons, 'b|':
		options	= 'Choice 1|Choice 2|Choice 3'; OR
		options	= {'Choice 1','Choice 2','Choice 3'};
	Radio-buttons, 'r|':
		options	= 'r|Choice 1|¤Choice 2|Choice 3'; 
		Note, option marked with ¤ is set as default selection.
	Popup-menu, 'p|':
		options	= 'p|Choice 1|¤Choice 2|Choice 3'; 
	Check-boxes, 'x|':
		options	= 'x|Choice 1|¤Choice 2|¤Choice 3'; 
		Note, options marked with ¤ are set ticked/checked as default.
	List-box, 'l|':
		options	= 'l|Choice 1|¤Choice 2|¤Choice 3'; 
	Slider:
		options = [startValue,endValue,defaultValue];
		Note, defaultValue is optional, if not supplied the slider is placed in the middle.
	Text-box, 't|':
		options = 't|My default text'; OR
		options = 't|My default text|with multiple|lines'; OR
		options = 't|1:1:25';
		Note, obvious numeric input (see third example) will be converted to numeric value(s).  
		
Multiple option groups:

	options	- cell of size = [N, 2]
	
	options{:, 1}	- Any of the above styles except for the push-button.
	options{:, 2}	- Subtitle placed above the options specified on the same row. 
					Note, leave empty or blank '' if no subtitle should be displayed. 
	Example:
		options	=	{'p|popup1|popup2', 'Popup subtitle'; ...
               'x|check1|check2', 'Checkbox subtitle'; ...
               [0, 1, 0.5], 'Slider subtitle'};

Output:

	choice - [double, string, cell] - selected option index, value(s) or text
	
Note, if no option is selected, the window is closed, or the cancel button is clicked choice is NaN.
If multiple option groups are supplioed, choice is a cell array of size [N, 1]. 
The selected option for each individual input type.

Advanced mode: 

	choice = menuN(mtitle, options, Opt)
	Opt - option structure which can be used to override default fontsizes, OK/Cancel button labels and gui sizes etc.
	Check the code for full list of options. 
	
	
See also:
	
	menu, inputdlg
