# NQueen-Solver

NQueen-Solver, you are, here, granted the permission to use the N queen solver freely.

The Solver contains three main parts
1. 
 basic object classes:
   
   a. Queen
   b. state
   c. point

 a solver class 

2. You can use the solver to solve the N-queen problem within a test class. The N is a inital parameter for using the solver.

3. The initial alignment is: All Queens are in the (i,i) diagnol. But,  you can customize it in the NQSolver class under the function named: buildInitial

4. The approach used in this solver is :simulate annealing. The probability of accepting wrose state satisfies boltzman distribution. 

5. The score of each state is calculated as the number of Queen conflicts. (1 point for 1 conflict)

6. As in my test, for 25x25 Queen problem, the best solution (0 conflicts ) can be found.

7. If the inital diagonal alignment is fine for you, just do 

      NQSolver nq=new NQSovler (N);
      
      nq.findGoal();
