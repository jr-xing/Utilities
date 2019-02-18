# Image Processing
## Image Normalization
```matlab
% MATLAB
function IsNormed = normImg(Is, varargin)
    normMethod = '01-naive';
    verbose = false;
    for argIdx = 1:2:length(varargin)
        argName = lower(varargin{argIdx});
        argValue = varargin{argIdx+1};
        switch(argName)
            case 'verbose'
                verbose = argValue;
            case 'method'
                normMethod = argValue;
            otherwise
                error(['normImg: input ' argName ' is not recognized!']);
        end
    end
    
    if verbose
        disp(['Normalizing images using method ' normMethod]);
    end
    
    switch normMethod
        case '01-naive'
            [H, W, N] = size(Is);
            IsNormed = zeros(H, W, N);
            for imgIdx = 1:N
                imgMin = min(min(Is(:,:,imgIdx)));
                imgMax = max(max(Is(:,:,imgIdx)));
                IsNormed(:,:,imgIdx) = (Is(:,:,imgIdx) - imgMin)/(imgMax-imgMin);
            end
        case '01'
            %IsNormed = (Is - min(Is)) ./ (max(Is) - min(Is));
            error(['normImg: method ' normMethod ' is not supported yet!'])
        case 'hist'
            error(['normImg: method ' normMethod ' is not supported yet!']);
        otherwise
            error(['normImg: method ' normMethod ' is not recognized!']);
    end
end
```
