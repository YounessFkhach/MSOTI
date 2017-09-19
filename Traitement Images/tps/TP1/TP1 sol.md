# TP 1

## ***Partie 1 : Traitement à partir de l’histogramme***

## Ex 1:
* L1 => H3
* L2 => H1
* L3 => H2


## Ex 2:
>Programmer et tester une fonction histogramme(image) qui retourne l’histogramme de l’image d’entrée.

```matlab
% histogramme.m

function hstgrm = histogramme(img)

[x,y] = size(img);
hstgrm = zeros(1,256);

for i=1:x
    for j=1:y
        index = img(i,j) + 1;
        hstgrm(1,index) = hstgrm(1,index) + 1;
    end
end
```
```matlab
% test_histogramme.m
% script de test du fonction historgamme(image)

img = Imread('coul.jpg');

hstgrm = histogramme(img);

subplot(1,3,1); % devision du fenetre
Imshow(img); % fonction d'affichage

subplot(1,3,2);
bar(hstgrm);

subplot(1,3,3);
imhist(img); % fonction histogramme de matlab
```

## Ex 3

### 1 )
> voir le fichier "TP1 Ex3.pdf"

### 2 )
>Programmer une fonction lin_histo(image) permettant de réaliser la linéarisation de l’histogramme

```matlab
% lin_histo.m

function final = lin_histo(source)

[x,y] = size(source);
target = zeros(x,y);

H = histogramme(source); % la fonction de l'Ex2

Min = min(source(:));
Max = max(source(:));

C = cumsum(H)/(x*y);

for i=1:x
    for j=1:y
        target(i,j) = (Max - Min) * C(source(i,j) + 1) + Min;
    end
end

final = uint8(target); % converstion du type pour avoir une image
```

```matlab
% test_lin_histo
% script de test du fonction lin_histo(image)

img = Imread('cameraman.tif');
resultat = lin_histo(img);

subplot(2,2,1);
Imshow(img);
subplot(2,2,2);
bar(histrogramme(img)); % affichage du histogramme d'image initiale

subplot(2,2,3);
Imshow(resultat);
subplot(2,2,4);
bar(histrogramme(resultat)); % histogramme du resulatat
```
___


## ***Partie 2 : Traitement par point***

### 1 : Rdynamique

```matlab
% Rdynamique.m

function final = Rdynamique(source)

source = double(source)
Min = min(source(:));
Max = max(source(:));

[x,y] = size(source);

target = zeros(x,y);

for i=1:x
    for j=1:y
        target(i,j) = 255*(source(i,j)-Min)/(Max-Min);
    end
end

final = uint8(target);
```

```matlab
% test Rdynamique

img = Imread('aquitain.gif');
resultat = Rdynamique(img);

subplot(1,2,1);
Imshow(img);

subplot(1,2,2);
Imshow(resultat);
```

### 2 : 
> multiplication de l'image par une constante `(x'(i,j)=x(i,j)*constante)`; 

```matlab
function final = multImage(source, const)

source = double(source);
[x,y] = size(source);

target = zeros(x,y);

for i=1:x
    for j=1:y
        x = source(i,j)*const;
        if x > 255 % ne pas depasse 255
            x = 255;
        end
        target(i,j) = x;
    end
end

final = uint8(target);
```

> correction logarithmique `(x'(i,j) = 255*log(x(i,j)+1)/log(256) )`;

```matlab
% ToDo

```

> correction gamma (avec gamma>1 et gamma<1) `(x'(i,j)=255*
x(i,j)^(1/gamma))`.

```matlab
% ToDo

```