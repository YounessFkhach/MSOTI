# TP 2

## I- Filtrage spatial

>Sur l’image ‘cameraman.tif’ ajoutez un bruit gaussien en utilisant la fonction imnoise() et sauvegardez l’image résultat. 

```matlab
img = Imread('cameraman.tif');
imgNoise = imnoise(img);
imwrite(imgNoise, 'noise.tif');
```

### I. Filtrage spatial linéaire
#### 1 : fonction filtre_Moy(image)

```matlab
% fonction filtre_Moy(image)

function final =  filtreMoy(source, n,m)

source = double(source);
[x,y] = size(source);

target = zeros(x,y);

window = zeros(n,m); % matrice de filtrage

height = floor(n/2); 
length = floor(m/2);

for i=1+height:x-height
    for j=1+length:y-length
        window = source(i-height:i+height,j-length:j+length);
        target(i,j) = mean(window(:));
    end
end

final = uint8(target);
```

#### 2 : fonction filtrage(image,H)

```matlab
% fonction filtrage(image,H)

function final = filtrage(source,H)

source = double(source);
[x,y] = size(source);

target = zeros(x,y);

[n,m] = size(H); % la taille du filtre est la taile du matrice a extraire
window = zeros(n,m);

length = floor(m/2);
height = floor(n/2);

for i=1+height:x-height
    for j=1+length:y-length
        window = source(i-height:i+height,j-length:j+length).*H; % '.*' pour la multiplication element par element
        target(i,j) = sum(window(:));
    end
end

final = uint8(target);
```
```matlab
% test du filtrage

img = Imread('cameraman.tif');
imgNoise = imnoise(img);

% les filtres:
H1 = [1,2,1;2,4,2;1,2,1]*(1/16); % suppression du noise
H2 =  [-1,-1,-1;-1,8,-1;-1,-1,-1]; % detection des contours
H3 =  [1,1,1;1,-8,1;1,1,1];

filtre1 = filtrage(imgNoise,H1); 
filtre2 = filtrage(img,H2);
filtre3 = filtrage(img,H3);

subplot(1,5,1);
Imshow(img);    % image initiale

subplot(1,5,2);
Imshow(imgNoise);   % image noise

subplot(1,5,3);
Imshow(filtre1);

subplot(1,5,4);
imshow(filtre2);

subplot(1,5,5);
imshow(filtre3);
```

#### 3 : Filtrage spatial non linéaire

```matlab
% ToDo
```