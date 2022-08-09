# some examples



### [Sequential Naming](https://github.com/m-bahrami/coding-101#variablesfilesfunctions-with-sequential-names-dynamically-variable-names)
```matlab
for i=1:3
    for j=1:2
    datalog.("foo"+i).("bar"+j) = i+j ;
    end
end
```

### [plot style and configurations](https://github.com/m-bahrami/coding-101#plot-style-and-configurations)
```matlab
%% =============== plot settings ===============

plt_font_size = 15;
% legend_font_size = 12;
Line_Width = 1.2;
Line_Width_Large = 2;

set(groot,'Defaultfigurecolor','w') % altr: set(gcf,'color','w');
set(0,'DefaultAxesXGrid','off')     % 0 is altr for groot
set(groot,'defaultAxesFontSize', plt_font_size)
set(groot,'defaultLineLineWidth', Line_Width)
set(groot, 'defaultAxesTickLabelInterpreter','latex'); 
set(groot, 'defaultLegendInterpreter','latex');
set(groot, 'DefaultTextInterpreter','latex');
% set(groot,'defaultLineLineWidth','remove') % resets to the default settings

% Ref. 
% https://www.mathworks.com/help/matlab/creating_plots/default-property-values.html#bug1auc
% https://www.mathworks.com/help/matlab/ref/startup.html
```
