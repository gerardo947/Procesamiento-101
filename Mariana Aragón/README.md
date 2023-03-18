# Procesamiento-101
Equipo MRI
%% Cargar imagen termal
f=imread("A2.jpg");
f=double(f(:,:,1));
f=f/max(max(f));
fx = figure(1);
imshow(f,[]);
colormap(fx,gray);
fx2 = figure(2);
imshow(f,[]);
colormap(fx2,hot);
figure(3)
[histdigital,binloc] = imhist(f);
plot(binloc,histdigital);
%% Conversion to centigrados
mintemp = 31; % Min temperature in image
maxtemp = 40; % Max temperature in image
temcent = (f-min(min(f)))/(max(max(f))-min(min(f)));
temcent = temcent*(maxtemp-mintemp)+mintemp;
fx3 = figure(4);
imshow(temcent,[mintemp,maxtemp]);
%lim([mintemp maxtemp]);
%axis([mintemp maxtemp]);
cmap = colormap(fx3,jet);
colorbar;
figure(5)
[histcent,binloc] = imhist(temcent,cmap);
plot(binloc,histcent);
