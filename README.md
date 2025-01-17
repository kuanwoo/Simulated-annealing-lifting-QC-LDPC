# Simulated Annealing lifting for QC-LDPC Codes and MET QC-LDPC Codes
Source code for article
Vasiliy Usatyuk und Ilya Vorobyev 
Simulated Annealing Method for Construction of High-Girth QC-LDPC Codes
 41st International Conference on Telecommunications and Signal Processing (TSP) 2018, 4-6 Jule, Athens, Greece.
 
It construct regular and irregular QC-LDPC codes with  multiple edge type circulants from protograph with required minimal EMD value. Short review (ENG) about Code on the Graph construction related problem http://www.mathnet.ru/php/presentation.phtml?option_lang=rus&presentid=17899.
 
Simulated annealing superior all currently published algoriths (PEG,QC-PEG, Fossorier-Declercq-Vasic Improved PEG, Yedidia Hill-Climbing) and  for construction QC-LDPC codes from capability of cycles broken, for detail read paper https://ieeexplore.ieee.org/document/8441303/  https://www.researchgate.net/publication/327194285_Simulated_Annealing_Method_for_Construction_of_High-Girth_QC-LDPC_Codes. With combination of code distance based sieving (for short and moderate code length) it allow to contruct QC codes with very good (probably best for current state of art) coding gain.


![alt text](https://github.com/Lcrypto/Simulated-annealing-lifting-QC-LDPC/blob/master/Figure.png)


Table I. Minimal value of circulant for regular mother matrix with row number m=3 and column number n with girth 10

|Column number|Simulated annealing|Hill Climbing|Improved PEG|Lower Bound|
|-------------|-------------------|-------------|------------|-----------|
|4|37|39|37|37|
|5|61|63|61|61|
|6|91|103|91|91|
|7|155|160|155|127|
|8|215|233|227|168|
|9|304|329|323|217|
|10|412|439|429|271|
|11|545|577|571|331|
|12|709|758|-|-|

Table II. Minimal value of circulant for regular mother matrix with row number m=3 and column number n with girth 12

|Column number|Simulated annealing|Improved PEG|Table V|
|-------------|-------------------|-------------|------------|
|4|73|73|97|
|5|160|163|239|
|6|320|369|479|
|7|614|679|881|
|8|1060|1291|1493|
|9|1745|1963|2087|
|10|2734|-|-|
|11|4083|-|-|
|12|5964|-|-|

Constructed regular codes represented at tables contained in file "high-girth regular LDPC results.zip". 

Constructed 8 cyclic group decomposition MET QC-LDPC Codes families based on 5G eMBB Base Graph 2 contained in folder "SA results".

Simulated annealing lifting for high girth QC-LDPC include EMD optimization of protograph, which allow to decrease error-floor (by eliminate harmful Trapping Sets), or improve waterfall properties (by lifting of protograph with better threshold).
To use application call binary file with command:

*binary -file Your_protograph_file -circulant size_of_circulant -upGirth check_condition_up_to_cycles -emd EMD_values -seed initial_value_for_random_generator -numberOfMatrices number_of_requirement_matrix -girth girth_size*

Your_protograph_file:

*Contain number of columns(Variable nodes), rows (Check nodes)*

*1, 0 value for circulant permutation block matrix, obtain by some optimization of LDPC codes ensemble (Density Evolution, Covariance Evolution, PEXIT chart and etc).*


For Example:
simulatedAnnealingEMD.exe -file proto.txt -circulant 500 -upGirth 8 -emd 20 -seed 123 -numberOfMatrices 1 -girth 8
Proto.txt contain base matrix:

*3 2*

*1 0 1*

*1 1 0*

For construction multiple edge use 2,3,..., edges instead 1. 
Example:

*simulatedAnnealingEMD.exe -file proto.txt -circulant 500 -upGirth 6 -emd 2 -seed 123 -numberOfMatrices 1 -girth 8*

*16 6*

*1 0 0 0 0 1 0 1 0 1 1 0 1 0 0 2*

*1 1 0 0 0 0 0 1 1 0 0 1 0 1 1 2*

*0 1 1 0 0 0 0 1 0 1 0 1 0 1 0 1*

*0 0 1 1 0 0 1 0 1 0 1 0 0 1 1 1*

*0 0 0 1 1 0 1 0 0 1 1 0 1 0 1 2*

*0 0 0 0 1 1 1 0 1 0 0 1 1 0 0 2*

output:

*16	6	500*

*440	-1	-1	-1	-1	0	-1	258	-1	203	0	-1	237	-1	-1	329&215*

*53	75	-1	-1	-1	-1	-1	95	0	-1	-1	443	-1	0	238	284&257*

*-1	104	363	-1	-1	-1	-1	67	-1	466	-1	5	-1	174	-1	425*

*-1	-1	265	249	-1	-1	363	-1	59	-1	392	-1	-1	324	119	488*

*-1	-1	-1	260	64	-1	429	-1	-1	383	402	-1	421	-1	348	97&222*

*-1	-1	-1	-1	429	480	86	-1	234	-1	-1	114	41	-1	-1	392&402*


How to compile:

For Linux: compile source code from 'linux' folder by 'run.sh' compile script.  


For Windows: compile by MS VS 2015 project at 'simulatedAnnealingEMD' folder. Windows binary file, and shell scripts to run examples of lifting at folder 'simulatedAnnealingEMD/x64/Release'. If you not install MS VS 2015 to run binary file simulatedAnnealingEMD.exe, don't forget to download and install redistributed kit from https://www.microsoft.com/en-us/download/details.aspx?id=48145.


P.S. Compare Simulated Annealing lifting for 8 girth with method from paper "A. Kharin, A. Dryakhlov, E. Mirokhin, K. Zavertkin, A. Ovinnikov and E. Likhobabin, "An Approach to the Generation of Regular QC-LDPC Codes with Girth 8," 2020 9th Mediterranean Conference on Embedded Computing (MECO), Budva, Montenegro, 2020, pp. 1-4".




Table III. Minimal value of circulant for regular mother matrix with row number m=3 and column number n with girth 8 with running time constrain less than 24 hours

|Column number|Simulated annealing|Ovinnikov et al|
|-------------|-------------------|-------------|
|4|9|9|
|5|13|13|
|6|18|18|
|7|21|21|
|8|25|25|
|9|30|30|
|10|35|35|
|11|40|40|
|12|42|45|



SA method constructed 3x12 regular code with girth 8 less than one hour on multitread (Amd Ryzen 3950x) and less than 21 hours on 1 thread (Intel i7700k), file "12_3_42girth8upGirth6emd0seed11protograph_from_proto.txt_matrix629558.txt", "12_3_42girth8upGirth6emd0seed333protograph_from_proto.txt_matrix828012.txt",  attached to github. 





Summary: SA lifting method still one of the best published QC-LDPC protograph lifting method from "flat" model(pure girth and girth+EMD maximization) of Trapping sets breaking.





With BR,
Vasiliy.

