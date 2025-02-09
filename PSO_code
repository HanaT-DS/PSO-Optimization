proc iml;
/*************** Defining objective funtions *****************/
start Rastrigin(X);
y=2*10 + (x[,1]**2-10*cos(2*constant("pi")*x[,1])) +
(x[,2]**2-10*cos(2*constant("pi")*x[,2]));
return y;
finish Rastrigin;
Start Sphere(x);
y=x*x`;
return (y);
finish Sphere;
Start fun(x);
y =10*(x[,1]-1)**2+20*(x[,2]-2)**2+30*(x[,3]-3)**2;
return (y);
finish fun;
/********constrained optimization*************/
/* Include this part of the code
if dealing with a constrained optimization problem */
/* Penalty function */
start penalty(x);
constraints = j(1, 2, 0);
constraints[1] = x[,1] + x[,2] + x[,3] - 5;
constraints[2] = x[,1]**2 + 2*x[,2] - x[,3];
penalties = j(1, ncol(constraints), 0);
do i = 1 to ncol(constraints);
if constraints[i] > 0 then penalties[i] = 1;
else penalties[i] = 0;
end;
return (sum(penalties));
finish penalty;
/*Penalized fitness function*/
start penalizedFitness(x);
penaltyValue = 10000; /* Penalty coefficient*/
obj = fun(x);
Ctr = penalty(x); /* Computes penalties based on constraints */
fitness = obj + penaltyValue * Ctr;
return (fitness);
finish;
/********* Defining Algorithm's parameters ***********/
dim = 2;
/*search space*/
ub = j(1,dim,5.12);
lb = j(1,dim,-5.12);
/* velocity limits*/
Vmax = j(1,dim,0.2*(ub[1]-lb[1]));
Vmin = -Vmax;
/*number of particules = swarm size*/
Nbpcl = 100;
/*maximum iteration*/
Maxiter= 200;
/*inertia*/
MaxW= 0.9;
MinW=0.4;
c1= 2; /*Personel acceleration factor*/
c2= 2; /*Social acceleration factor*/
/****************** Initialization ******************/
pclPos = j(Nbpcl, dim, 0);
pclVel = j(Nbpcl, dim, 0);
pclCost = j(Nbpcl, 1, 0);
pclBestPos = j(Nbpcl, dim, 0);
pclBestCost = j(Nbpcl, 1, constant("big"));
GBestPos = j(1, dim, 0);
GBestCost = constant("big");
call randseed(1234);
do i = 1 to nbpcl;
do j = 1 to dim;
pclPos[i,j] = (ub[1,j]-lb[1,j])
*randfun(1, "Uniform")+lb[1,j];
pclVel[i,j] = (Vmax[1,j]-Vmin[1,j])
*randfun(1, "Uniform")+Vmin[1,j];
pclCost[i] = Rastrigin(pclPos[i,]);
end;
end;
/* Initialize the personal best of each particle */
do i = 1 to nbpcl;
pclBestPos[i,] = pclPos[i,];
pclBestCost[i] = pclCost[i];
end;
/* Initialize the global best */
do i = 1 to nbpcl;
if pclBestCost[i] < GBestCost then do;
GBestCost = pclBestCost[i];
GBestPos = pclBestPos[i,];
end;
end;
/******************* Main Loop of PSO *****************/
do it = 1 to Maxiter;
do i = 1 to nbpcl;
W = MaxW - it*((MaxW-MinW)/Maxiter);
/* Update Velocity */
u1 = j(Nbpcl, dim, 0);
u2 = j(Nbpcl, dim, 0);
call randgen(u1, "UNIFORM");
call randgen(u2, "UNIFORM");
pclVel[i,]=W*pclVel[i,] + c1*u1[i,]#
(pclBestPos[i,]-pclPos[i,]) +c2*u2[i,]
#(GBestPos- pclPos[i,]);
/* Apply Velocity Limits */
do d=1 to dim;
if pclVel[i,d] > Vmax[,d] then do;
pclVel[i,d]= Vmax[,d];
end;
if pclVel[i,d] < Vmin[,d] then do;
pclVel[i,d]= Vmin[,d];
end;
end;
/* Update Position */
pclPos[i,] = pclPos[i,] + pclVel[i,];
/* Apply Position Limits */
do d=1 to dim;
if pclPos[i,d] > ub[,d] then do;
pclPos[i,d]= ub[,d];
end;
if pclPos[i,d] < lb[,d] then do;
pclPos[i,d]= lb[,d];
end;
end;
/* Evaluation : Update Cost */
pclCost[i] = Rastrigin(pclPos[i,]);
/* Update Personal Best */
if pclCost[i] < pclBestCost[i] then do;
pclBestPos[i,] = pclPos[i,];
pclBestCost[i] = pclCost[i];
/* Update Global Best */
if pclBestCost[i] < GBestCost then do;
GBestCost = pclBestCost[i];
GBestPos = pclBestPos[i,];
end;
end;
end;
GBestCosts = GBestCosts // GBestCost;
end;
/* Output Results */
print "The Final Global Best Position is : ";
print GBestPos;
print "The Final Global Best Cost (The Global Minimum) is :";
print GBestCost;
print "The Global Best Cost per iteration is :";
print GBestCosts;
quit;
