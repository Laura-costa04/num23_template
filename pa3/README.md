% a)

% Abgabe von: laura.costa(maria-laura.costa@student.uni-tuebingen.de),
% Shafi Ahmad (amtul-shafi.ahmad@student.uni-tuebingen.de)

%Implementiere die Funktion NewtonInter(x,v,u) für zwei übergebenen
%Vektoren x,y Element von R^(n+1), die die Punkte (xi,yi) für i=o,...,n
%beinhalten. Die Funktion berechnet die Koeffizienten c des Newton-IPP p
%und die Funktionserte v für die Eingabenvektoren x,y und u. 

% Die dividierten Differenzen werden mit einer doppelten Schleife berechnet
% ,und die Funtkionserte werden mit einer einfachen Schleife berechnet. 


function[v,c]= NewtonInter(x,y,u)
n=lenght(x)-1;
c=y;
for j=1:n
    for i=n+1:-1:j+1
        c(i)=(c(i)-(i-1))/(x(i)-x(i-j));
    end
end
v=c(n+1)*ones(size(u));
for j=n:-1:1
    v=c(j)+(u-x(j)).*v;
end
end

%b) 

% Abgabe von: laura.costa(maria-laura.costa@student.uni-tuebingen.de),
% Shafi Ahmad (amtul-shafi.ahmad@student.uni-tuebingen.de)

%Die Funktion kann wie folgt implentiert werden , wobei die Funktion f(x)
%den Wert von f(x) füreinen gegebenen Wert von x nerechnet.

% Mit den Punktoperator kann man die Elemetweise-Operatoren durchführen

function y= f(x)
    y=1./(1+25*x.^2);
end

%c)

% Abgabe von: laura.costa(maria-laura.costa@student.uni-tuebingen.de),
% Shafi Ahmad (amtul-shafi.ahmad@student.uni-tuebingen.de)

%Der Skript implementiert die Funktion f im Intervall [-1,1], indem man die
%Stützstellen xi mit i=o,...,n für alle n=4,8,12 verwendet.Dabei werden die
%geeigneten Schaubilder von f geplottet


%Stützstellen
n_values=[4,8,12];
for n =n_values
    x=cos(2*(0:n)+1*pi/(2*n+2));
    y=f(x);

%Interepolation
u=linespace(-1,1,1000);
[v,~]=NewtonInter(x,y,u);

%Plotting
figure;
plot(u,f(u),'LineWidth',2);
hold on;
xlable('x');
ylable('y');
title(sprintf('Interpolation von f mit n=%d',n));
legend('f(x)','p(x)');

%Error plot
figure;
plot(u,abs(f(u)-v),'LineWidth',2);
xlable('x');
ylable('/f(x)-p(x)/');
title(sprintf('Interpolationsfehler von f mit n=%d',n));
end





