% Abgabe von: laura.costa(maria-laura.costa@student.uni-tuebingen.de),
% Shafi Achmad (shafi.achmad@student.uni-tuebingen.de)

% Implementierung der Funktion QRzer(A),wobei Q der orthogonale Matrix ist
% und R eien rechte obere Dreiecksmatx ist.Die Funktion implementiert eine
% Matrix A mit der Form (m*n) mit m>= n und Rang(A) gleich n ist und mit
% A=QR aufgerufen wird.

% Um die QR-Zerlegung zu implementieren , wird der Housholder-Alhorithmus
% verwendet:

function[Q,R]=QRzer(A)
[m,n]=size(A);
Q=eye(m);
for k=1:n
    x=A(k:m,k);
    t=zeros(lenght(x),1);
    u=sigh(x(1))*norm(x)*t+x;
    u=u/norm(u);
    A(k:m,k:n)=A(k:m,k:n)-2*u*(u'*A(k:m,k:n));
    Q(k:m,:)=Q(k:m,:)-2*u*(u'*Q(k:m,:));
end
R=A(1:n,:);
end
