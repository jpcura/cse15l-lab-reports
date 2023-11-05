**Part 1 - Bugs**
* A failure-inducing input for the buggy program
  ```
   @Test
  public void testRevereInPlace2(){
  int[] input1 = {1, 2, 3, 4};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{4, 3, 2, 1}, input1);
  }
  ```
* An input that doesn't induce a failure
  ```
  @Test
  public void testReverseInPlace3(){
  int[] input1 = {1};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[] {1}, input1);
  }
  ```
  
* The symptom

  <img width="481" alt="image" src="https://github.com/jpcura/cse15l-lab-reports/assets/146609257/8814c314-ddec-4dd2-9048-bd0824c3f8fb">
  

* The bug

```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

changed to:

```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] newarr = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newarr[i] = arr[arr.length - i - 1];
      
    }
    for (int i = 0; i < arr.length; i += 1){
      arr[i] = newarr[i];
    }
  }
```

Why the fix addresses the issue: The bug was that `reverseInPlace(int[] arr)` would replace the contents in the original array so that after iterating through half, the original contents of the second half would not get reversed and instead the new contents would get copied over. The fix is creating `newarr[int]` which first copies the contents of the original array in reverse order without overwriting `arr[int]`. The contents in `newarr[int]` can then be copied into `arr[int]`.



**Part 2 - Research Commands**
**`grep`**

`grep -n`

```
#input (using bash):

find technical/biomed > findlr3.txt
xargs grep -n "Infection" < findlr3.txt

#output:

$ bash lr3.sh
grep: technical/biomed: Is a directory
technical/biomed/1468-6708-3-3.txt:252:        The Pravastatin or Atorvastatin Evaluation and Infection
technical/biomed/1468-6708-3-3.txt:293:        Evaluation and Infection Therapy.
technical/biomed/1471-2121-3-22.txt:212:          the F-box (Ad-SKP2-ΔF). Infection of asynchronous LNCaP
technical/biomed/1471-2180-1-28.txt:339:          infection. Infections were typically at an MOI of 0.01
technical/biomed/1471-2180-2-26.txt:22:        pathogenic factor. Infection of cultured podocytes with
technical/biomed/1471-2180-3-5.txt:663:          Infection and invasion assay
technical/biomed/1471-2202-2-3.txt:408:          Infection of monocytic cells with HIV
technical/biomed/1471-2334-1-9.txt:6:        Infection with human immunodeficiency vims (HIV) elicits
technical/biomed/1471-2334-2-29.txt:6:        Infection with the hepatitis C virus (HCV) occurs
technical/biomed/1471-2407-2-15.txt:394:          receptors (Figure 4). Infection with the WT virus leads
technical/biomed/1471-2407-2-15.txt:396:          phosphorylation. Infection with the MK virus eliminated
technical/biomed/1471-2431-2-1.txt:104:          and (9) encephalopathy. Infection associated with at
technical/biomed/1471-2458-1-9.txt:115:        codes for Lower Respiratory Infection (LRI) currently in
technical/biomed/1471-2458-3-11.txt:75:        California Emerging Infections Program (CEIP) active
technical/biomed/1471-2458-3-11.txt:102:          Emerging Infections Program (EIP). The California EIP
technical/biomed/1471-2458-3-20.txt:38:          Duke Infection Control Outreach Network (DICON). The
technical/biomed/1471-2466-1-1.txt:267:        Infection Study Group [ 4 ] , 94% of the patients with PCP
technical/biomed/1471-2466-1-1.txt:356:        Infection Study Group has shown upper respiratory infection
technical/biomed/1471-2466-2-4.txt:9:        in developing countries [ 2 ] . Infection with the human
technical/biomed/1472-6769-1-3.txt:12:        death [ 2 3 4 5 6 ] . Infection of
technical/biomed/1475-2883-2-11.txt:284:        (Table 4). Infection prevalence in Leogane decreased from
technical/biomed/ar429.txt:306:        Infection with CMV is ubiquitous within the human
technical/biomed/cc1498.txt:170:          retrospectively from the raw data. Infections were
technical/biomed/cc1843.txt:115:        blood cultures were positive. Infections were
technical/biomed/cc2358.txt:6:        Infections with resistant organisms represent a serious
technical/biomed/gb-2002-4-1-r2.txt:653:          Infections
technical/biomed/gb-2002-4-1-r2.txt:670:          to antibiotic-free Caco-2 monolayers. Infections were
technical/biomed/gb-2002-4-1-r2.txt:690:          Infections were carried out under the guidelines of a
```

```
#input:
find technical/biomed > findlr3.txt
xargs grep -n "Infection of" < findlr3.txt

#output:
$ bash lr3.sh 
grep: technical/biomed: Is a directory
technical/biomed/1471-2121-3-22.txt:212:          the F-box (Ad-SKP2-ΔF). Infection of asynchronous LNCaP
technical/biomed/1471-2180-2-26.txt:22:        pathogenic factor. Infection of cultured podocytes with
technical/biomed/1471-2202-2-3.txt:408:          Infection of monocytic cells with HIV
technical/biomed/1472-6769-1-3.txt:12:        death [ 2 3 4 5 6 ] . Infection of
```
* `grep -n` searches for the pattern and gives the line number within the file where the pattern is found. This is useful since we can more quickly fine where our desired pattern is within a `.txt` file. 
* source: https://www.gnu.org/software/grep/manual/grep.html

`grep -v`
```
#input:
find technical > findlr301.txt
grep -v ".txt" findlr301.txt

#output:
$ bash lr301.sh 
technical
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```

```
#input:
find technical > findlr301.txt
grep -v "technical" findlr301.txt

#output
$ bash lr301.sh 

```
* `grep -v` gives lines that don't contain the patterns provided. This may be useful if you want to find, as in the first examples the directories instead of `.txt` files. Or, if you want to find anything that you don't want in the file, for instance, if we want all of our files to contain `technical`.
* source: https://www.gnu.org/software/grep/manual/grep.html


`grep -m`
  
```
#input:
find technical > findlr301.txt
grep -m 4 "technical" findlr301.txt

#output:
$ bash lr301.sh 
technical
technical/911report
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
```

```
#input:
find technical > findlr301.txt
grep -m 10 "technical" findlr301.txt

#output:
$ bash lr301.sh 
technical
technical/911report
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
```
* `grep -m` limits the amount of output by the number given after. This may be useful if one is expecting a lot of output and wants to limit the amount of information given. It also may be useful when displaying output so that the example is not too long.
* source: https://www.gnu.org/software/grep/manual/grep.html

`grep -i`

```
#input pwd(../technical/biomed):
find *.txt > findlr301.txt
xargs grep -i "AUTONOMIC NERVOUS SYSTEM" < findlr301.txt

#output
$ bash ../../lr301.sh
1471-2202-3-19.txt:        analgesia, hibernation, autonomic nervous system function,
1472-684X-1-5.txt:          results from stimulation of the autonomic nervous system
```
```
#input:
find *.txt > findlr301.txt
xargs grep -i "diseASEd" < findlr301.txt

#output:
$ bash ../../lr301.sh
1471-2164-3-7.txt:        limited to, (i) comparisons of healthy and diseased tissue
1471-2180-2-26.txt:          hyperplastic nephrons in the diseased transgenics versus
1471-2180-2-26.txt:          during the proliferation of epithelium in diseased
1471-2415-3-4.txt:        initial clinical utilization was removal of diseased
1472-6831-2-2.txt:          diseased subjects were therefore increased compared to a
1472-6831-2-2.txt:          and no severely diseased subjects. Clearly, combining
ar104.txt:          which treatment of a diseased joint by
ar430.txt:        hTNF-α production in the diseased joint. Additionally, 
ar430.txt:        local diseased tissues either through suppression of   
ar430.txt:        diseased joint, which is consistent with previous findings
ar745.txt:        effects of TGF-β1 in both diseased knee joints and normal
ar745.txt:        particular, in diseased joints. Moreover, it appears as if
ar792.txt:        diseased tissue. When these cells were cultured with medium
ar792.txt:        basal state, unaffected by the environment of the diseased
ar795.txt:        vary somewhat between HSFs from OA, RA, and nondiseased
bcr620.txt:        diseased tissue and in samples of normal breast tissue.
gb-2001-2-6-research0021.txt:        and the frequency of occurrence of diseased individuals, it
gb-2003-4-4-r24.txt:          2 ) found in diseased individuals is
gb-2003-4-4-r24.txt:          2 among diseased individuals (
gb-2003-4-4-r24.txt:          where diseased individuals are compared to individuals
```
* `grep -i` ignores the case status of the pattern given. This is useful as some words that are searched for may be at the beginning of the sentence or all-caps title.
* source: https://www.gnu.org/software/grep/manual/grep.html


