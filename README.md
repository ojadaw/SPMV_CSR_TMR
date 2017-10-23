# SPMV_CSR_TMR
Implementation of the TMR on the Compressed Sparse Row (CSR) format for the SPMV
The project is meant for dependable computing project. It implements a Tripple Modular Redundancy (TMR) algorithm for 
the Sparse Matrix -Vector Multplication. The TMR, replicates the memory array that carries the CSR values. The CSR values are
non-zeros (data) values from the sparse matrix (matrix shown below), the index column (lebeled index inthis code) of each non-zero 
value from the matrix, and the potiner to the non-zero values. The pointer is calculated based on the CSR format. 
Thus, let Ptr =  pointer, then Ptr = Ptr[i-1] + # of row for that non-zero value. 
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

The CSR_Arrays (3 copies for TMR) have been loaded (ROM) with the CSR format values, thus non-zero values, Index, and the Ptr. In this case, it makes it easier without actaully performing the CSR format in RTL. 

Update version will implement the CSR format in RTL.

There are 3 voters, 1 for the CSR non-zero values, 1 for the CSR index, and the other compares ptr of the non-zero vaues. Each voter compers the 3 copies of the CSR data, and outputs the majority (if all agrees, 3-out-3,). The minimum good output for the voter is to output 2-out-3. Thus if 2 inputs agree, it disregards the other one and outputs 1 of the 2 agreed input.
