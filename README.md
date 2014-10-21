matlab_menu_gui
===============

A powerful but simple to use graphical user interface menu in Matlab. Combines the functionality of menu (exclusive option selection) and inputdlg (text input) as well as introducing radio-button groups, check-boxes and sliders.

%% menuN An alternative to Matlab's menu function with added functionality
%   
% Syntax:
%  choice = menuN(mtitle, options)
%  choice = menuN(mtitle, options, Opt)
%
% Input:
%  mtitle   - [string]  - Menu window title 
%  options  - [various] - Multifunctional: 
%     (b) [cellstr]: Buttons are created with labels as in the cell array.   
%     ex. options = {'option1', 'option2', ... },
%     OR: options = 'b|option1|option2|...', results in:
%           |--mtitle---------|
%           |  [  option1  ]  |
%           |  [  option2  ]  |
%           |  [    ...    ]  |
%           |-----------------|
%     (r) [string && options(1:2) == 'r|' ]: 
%           Radiobuttons for single selection, separate options with |:      
%           Start an option string part with ¤ to have it default toggled on.    
%     ex. options = 'r|option1|¤option2|...', results in:
%           |--mtitle--------|
%           |  O  option1    |
%           |  x  option2    |
%           |  O     ...     |
%           |  [    OK    ]  |
%           |----------------|
%     (p) [string && options(1:2) == 'p|' ]: 
%           Popupmenu for single selection, separate options with |:      
%           Start an option string part with ¤ to set it default toggled on.    
%     ex. options = 'p|option1|option2|...', results in:
%           |--mtitle--------|
%           |  | optionX |v| |        
%           |  [    OK     ] |
%           |----------------|
%     (x) [string && options(1:2) == 'x|' ]: 
%           Checkboxes with mutliselection, separate options with |:      
%           Start an option string part with ¤ to set it default toggled on.    
%     ex. options = 'x|option1|¤option2|...', results in:
%           |--mtitle--------|
%           | | | options    |
%           | |x| options    |
%           | | |    ...     |
%           | [    OK     ]  |
%           |----------------|
%     (l) [string]: Listbox with mutliselection, separate options with |.    
%           Start an option string part with ¤ to set it default toggled on.    
%     ex. options = 'option1|option2|...', results in: 
%           |--mtitle----------|
%           |  |  option1  |   |
%           |  |  option2  |   |
%           |  |    ...    |   |
%           |  [    OK     ]   |
%           |------------------|
%     (s) [double, length == 2]: Slider is created from initial to final value.
%      or [double, length == 3]: Same slider but with third value as default
%     ex. options = [0,7,3.5], results in: 
%           |--mtitle--------------|
%           | |<|====[]====|>| 3.5 |
%           | [        OK        ] |
%           |----------------------|
%     (t) [string && options(1:2) == 't|' ]:
%           Input text box, returns string inputed into text box. 
%     ex. options = 't|my text|the second line', results in: 
%           |--mtitle--------------|
%           | | my text          | |
%           | | the second line  | |
%           | [        OK        ] |
%           |----------------------|
%     (*) [cell-Nx2]: Multiple "choice groups" in the same menu:
%           Each cell element should have any of the syntaxes as above. 
%           A gui menu window is then created with all of these selections of 
%           choices. The second column of the cell should contain a subtitle for
%           the corresponding choice group. If the second input is empty no 
%           subtitle is printed. The pushbutton type menu group (b) is changed
%           to a popupmenu selection (p) instead of pushbuttons. Example:
%     ex. options = {'p|option1|option2|...','subititle1';...
%                    'options2 part1|options2 part2','subtitle2';...
%                    [0,7,3.5],'subtitle3'}, results in: 
%           |--mtitle---------------|
%           |  subtitle1            |
%           |  | options1     |v|   |        % Popupmenu (instead of buttons)
%           |  subtitle2            |
%           |  | options2 part1 |   |        % Listbox
%           |  | options2 part2 |   |
%           |  subtitle3            |
%           |  |<|===[]===|>| 3.5   |        % Slider
%           |  [       OK       ]   |
%           |-----------------------|
%  Opt    - [struct]  - Structure containing options for font name, size etc.
%
% Output:
%  choice - [double OR cell IF multiple options] - selected option(s)
%     (a) If multiple selection groups are used as by input of type (5) choice 
%         is a cell array equal with length == number of rows in options.
%     (b) If an selection type allows multiselection the choice array
%         contains all selected options, (array instead of scalar).
%     (c) If any option group has no values selected its value is -1.
%  
% Example of usage with input of type (*):
%  choice = menuN('menuN',...
%        {  [1,2,1.75], 'Loss Parameter:';   ...
%           'r|optA1|op2|¤defasdfasdfa','Operating Model:';...
%           'p|a|b|¤c','Select a, b or c:';...
%           'x|Use1|¤Use2|¤Use3','Use methods:';...
%           't|first test|all is ok','Comment:'});
%  If OK is selected directly we are returned the following choice:
%   choice = 
%        [    1.7500]
%        [         3]
%        [         3]
%        [2x1 double] % == [2;3];
