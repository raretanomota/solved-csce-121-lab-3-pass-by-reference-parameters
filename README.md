Download Link: https://assignmentchef.com/product/solved-csce-121-lab-3-pass-by-reference-parameters
<br>
The aim of this lab is to continue getting practice in writing functions. There are questions which emphasize the use of pass-by-reference parameters as a useful way to operate on data. Additionally, this lab will give you plenty of practice with arrays.

How far must I get?

As before, this lab is assigned for the entire week. It is wise to look over the questions and to make a first attempt at some of them before arriving at your lab session. This way you can optimize your lab time, getting help with the questions that are most tricky for you. You’re expected to complete the questions that you’re not able to finish in the lab on your own.

<h2>Pass-by-reference</h2>

<h3>Ordering a pair</h3>

Write a function order_pair that takes two int parameters x and y and swaps them if x &gt; y.

<h3>Ordering a triple</h3>

Using your order_pair write a function three_in_a_row that takes three int parameters x, y, and z. Using pass-by-reference, have the function place its inputs in non-decreasing order so that after calling your function you have x ≤ y ≤ z. (Accomplish this without using an array.)

<h2>Reversing a list in place</h2>

Given an array of integers, write a function which changes the input so that the integers now appear in reverse order. The objective here is to do this <em>in place</em>, which means using only the input array and without making any new array of values.

The following gives an appropriate declaration for the function.

void rev_list(int input[], int num){ // Takes input, a list with num entries  // Alters input so that the entries are in reverse order    …}

The preceding declaration might be a bit of a surprise. First, we tell the compiler that we’re expecting an argument that is an array of ints, but we don’t need to specify its size beforehand. (Which is just as well, as we don’t want to have to write separate functions for arrays of size 10, and another for arrays of size 11, and another for 12, and so on.) Secondly, even though we’ll be modifying the parameter input we don’t put an ‘&amp;’ before the name because arrays are automatically passed by reference.

<table>

 <tbody>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td>

    <table>

     <tbody>

      <tr>

       <td>Does your rev_list work on lists whose length is odd, as well as those whose length is even?Does it work on input list of length 1?Does it work on input list of length 0?</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

<h2>Craps</h2>

These are the rules of a simple game of craps.You roll a pair of dice. Suppose that the sum of their faces is V.

<ul>

 <li>If V=7 or 11, the player wins.</li>

 <li>If V=2, 3, or 12, the house wins.</li>

 <li>If V=4, 5, 6, 8, 9, or 10, then you do the following:

  <ul>

   <li>Keep rolling until you get a sum of V or 7.</li>

   <li>If it was V, the player wins.</li>

   <li>But if 7 comes up first, the house wins.</li>

  </ul></li>

</ul>

Suppose that you’re running a casino that has a special dice machine which outputs a fixed sequence of dice rolls. These are represented by an array of ints. Write a function which, given such an array, reports whether (i) the player wins; (ii) the player loses; or (iii) more rolls are still needed.

Write your code to be robust to incorrect inputs. It should check that the array inputs really are within the 1-6 range for a standard die, outputting an error if things aren’t correct.

<h2>Polynomials</h2>

One convenient way to represent a polynomial is as an array of coefficients. For example P<sub>1</sub> a polynomial of degree 4 in x defined by P<sub>1</sub>(x) = 2.3 x<sup>4</sup> + 1.2 x<sup>2</sup> – 9.3 x + 8.4 can be expressed with five floating-point values stored in an array: {2.3, 0.0, 1.2, -9.3, 8.4}.

It is important notice the ordering of the coefficients and also the need to explicitly include zero values for missing terms to ensure that the position in the array implicitly gives the power of x associated with the coefficient.

<h3>Pretty printing polynomials</h3>

A good step in understanding some new representation of data is to find ways to display it. Your first task is to write a function which will give an attractive, easily readable presentation of the polynomial. Your function should print the following for P<sub>1</sub>:

P_1(x) = (2.3)*x^4 + (1.2)*x^2 + (-9.3)*x + (8.4)

Here’s some skeleton code to get you started:

#include &lt;iostream&gt;using namespace std; const int max_degree = 15; void pretty_print_poly(float coeffs[], int degree){ // A function to write a nicely formatted version of the polynomial to cout    …} int main(){    float p1_coeff[max_degree] = {2.3, 0.0, 1.2, -9.3, 8.4};     cout &lt;&lt; “P_1(x) = “;    pretty_print_poly(p1_coeff, 4);    cout &lt;&lt; endl;     return 0;}

<h3>Evaluating polynomials</h3>

Of course we’d like to be able to do more than just print polynomials. Write a function poly_eval to evaluate a polynomial at a given value of x.

float power(float b, int exp){ // computes b^exp  // (Insert your code from the previous lab)} float poly_eval(float coeffs[], int degree, float x){ // evaluates a polynomial at x. The polynomial representation has  // taking in degree+1 coefficients in coeffs, with the highest degrees  // appearing first.    …}

<h3>Horner’s method</h3>

Horner’s method for evaluating polynomials can be more efficient than the direct approach. It exploits the fact that any polynomial can be rewritten in order to save having to raise x to any power. Using the same polynomial as before as an example, we unroll it as follows:P<sub>1</sub>(x) = 2.3 x<sup>4</sup> + 1.2 x<sup>2</sup> – 9.3 x + 8.4= (2.3 x<sup>3</sup> + 0.0 x<sup>2</sup> + 1.2 x – 9.3)x + 8.4= ((2.3 x<sup>2</sup> + 0.0 x + 1.2)x – 9.3)x + 8.4= (((2.3 x + 0.0)x + 1.2)x – 9.3)x + 8.4The steps involved in getting to the final expression are not important for the code, but they help show how one arrives at the final expression.

Implement Horner’s method and use your code from eval_poly_simple to help you verify that it is correct.

float horners_method(float coeffs[], int degree, float x){ // evaluates a polynomial at x. The polynomial representation has  // taking in degree+1 coefficients in coeffs, with the highest degrees  // appearing first.    …}

<h3>Polynomial derivatives</h3>

Write a function which, given an array and the degree of the polynomial, alters the array and degree argument so that they represent the polynomial resulting from taking the derivative of the input (once, with respect to the sole variable).

Don’t return a new array, but modify the one passed as input. It might be helpful, as a first step, to keep the same number of entries in the output as the input (hence, keeping the degree fixed). Once that is working, you should try to use one fewer entry in the array.

<table>

 <tbody>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td>

    <table>

     <tbody>

      <tr>

       <td>Since you’re updating the degree, you’ll need to pass that by reference:void poly_d_by_dx(float coeffs[], int &amp;degree)</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

<h2>Computing the mode and median of a list</h2>

Suppose that you are given an array of n integers, each between 1 and 20, inclusive. In the following questions, you’re asked to compute a summary statistic—try to do this with a single pass over the input array and, specifically, do this <em>without</em> sorting the list. Also, if the input contains numbers that are not within the prescribed range (i.e., not in 1-20), catch this fact and output an error message.

<h3>Mode of a list</h3>

The <a href="https://en.wikipedia.org/wiki/Mode_(statistics)"><em>mode</em></a> of a collection of numbers is the number which occurs most often. Write a function that returns the mode of the array. If there are multiple such numbers, break the ties by returning the smallest number.

int calc_mode(char list[], int n){ // computes the mode, list is assumed to have n numbers 1 &lt;= x_i &lt;= 20    …}

Median of a list

The <a href="https://en.wikipedia.org/wiki/Median"><em>median</em></a> of a collection of numbers is the number which separates the lower half of the numbers from the upper half. Write a function that returns the median of the array. If <em>n</em> is odd, the median is a number in the array. If <em>n</em> is even it may or may not be in the array.