# Text Processing
## IO
## Read text file
```matlab
% 1. Read in whole file at one time
% See function fscanf() and textscan()

% 2. Read file line by line
% Use fgetl()
% https://www.mathworks.com/matlabcentral/answers/71374-how-to-read-a-text-file-line-by-line
fileID = fopen(filename,'r');
while true
    line = fgetl(fileID);
    line = line(line~=' ');
    if ~ischar(line)
        break;
    end
    lines{end+1} = line;        
end
fclose(fileID);
```

## Processing
### Remove Whitespaces
```matlab
% From:
% https://www.mathworks.com/matlabcentral/answers/43638-remove-spacing-in-a-string
line = line(line ~= ' ');
```
