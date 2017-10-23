# SPMV_CSR_TMR
Implementation of the TMR on the Compressed Sparse Row (CSR) format for the SPMV
The project is meant for dependable computing project. It implements a Tripple Modular Redundancy (TMR) algorithm for 
the Sparse Matrix -Vector Multplication. The TMR, replicates the memory array that carries the CSR values. The CSR values are
non-zeros (data) values from the sparse matrix (matrix shown below), the index column (lebeled index inthis code) of each non-zero 
value from the matrix, and the potiner to the non-zero values. The pointer is calculated based on the CSR format. 
Thus, let Ptr =  pointer, then 
               Ptr = Ptr[i-1] + # of row for that non-zero value. 
 Example:
For a Sparse Matrix


                          1 2 0 0 0 10 0 0    
                          0 0 1 0 0 1 2 0     
                          0 2 0 0 5 0 0 10    
             A =          0 0 6 0 1 0 0 11    
                          0 0 0 8 0 7 0 22    
                          0 2 0 0 5 0 0 1     
               
 Data  = [1 2 10 1 1 2 2 5 10 6 1 11 8 7 22 2 5 1]
 Index = [0 1 5  2 5 6 1 4  7 2 4  7 3 5  7 1 4 7]    
 Ptr   = [0 3 6  9 12 15 18] 
