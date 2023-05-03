Download Link: https://assignmentchef.com/product/solved-cs-3430-homework5-partial-differential-equations
<br>
Write a function solve_pdeq(k1, k2) that takes the values of <em>k</em><sub>1 </sub>and <em>k</em><sub>2 </sub>in the partial differential equation <em>k</em><sub>1</sub><em>y</em><sup>0 </sup>= <em>k</em><sub>2</sub><em>y </em>and returns a function representation of a solution to this partial differential equation.

Write a function solve_pdeq_with_init_cond(y0, k) that takes two constants y0 and k such that <em>y</em><sup>0 </sup>= k<em>y </em>and y0 = <em>y</em>(0) and returns a function representation of a solution to the partial differential equation with the specified initial condition.

Save your code in hw05.py

<h2>Test 01</h2>

Solve <em>y</em><sup>0 </sup>= <em>y</em>.

def test_01(self):

print(’
***** Unit Test 01 *****’) eq = solve_pdeq(make_const(1.0), make_const(1.0)) assert not eq is None print(eq) eqf = tof(eq) assert not eqf is None err = 0.0001 gt = lambda t: math.e**t for t in range(100):

assert abs(gt(t) – eqf(t)) &lt;= err

print(’Unit Test 01: pass’)

Here is the output of test_01 in the Py shell.

***** Test 01 ************

1.0*(2.71828182846^(1.0*(t^1.0)))) Test 01: pass

<h2>Test 02</h2>

Solve 4.

def test_02():

print(’
***** Unit Test 02 *****’) eq = solve_pdeq(make_const(4.0), make_const(1.0/3.0)) assert not eq is None print(eq) eqf = tof(eq) assert not eqf is None gt = lambda t: math.e**((1.0/12.0)*t) for t in range(100):

assert abs(gt(t) – eqf(t)) &lt;= 0.0001

print(’Test 02: pass’)

Here is the output of test_02 in the Py shell.

***** Test 02 ************

(1.0*(2.71828182846^(0.0833333333333*(t^1.0)))) Test 02: pass

<h2>Test 03</h2>

Solve <em>y</em><sup>0 </sup>= 3<em>y</em>; <em>y</em>(0) = 1.

def test_03():

print(’
***** Unit Test 03 *****’) eq = solve_pdeq_with_init_cond(make_const(1.0),

make_const(3.0))

assert not eq is None print(eq) eqf = tof(eq) assert not eqf is None def gt(t): return math.e**(3.0*t) err = 0.0001 for t in range(100):

assert abs(gt(t) – eqf(t)) &lt;= err

print(’Test 03: pass’)

Here is the output of test_03 in the Py shell.

***** Test 03 ************

1.0*(2.71828182846^(3.0*(t^1.0)))) Test 03 pass

Use the examples we worked out in lecture 9 and in the reading handout to write more unit tests.

<h1>Problem 2: Growth Models for Bacteria Cultures</h1>

Write a function find_growth_model(p0, t, n) that takes three constants and determines growth models for various bacteria cultures. Specifically, it returns a function representation of the exponential growth model for a bacteria culture described by the given parameters. You may assume that each culture is modeled with <em>P</em>(<em>t</em>) = <em>P</em>(0)<em>e<sup>kt</sup></em>, where <em>P</em>(0) = p0, <em>t </em>is a number of hours, and <em>n </em>is a constant specifying how fast the initial population <em>P</em>(0) has grown after <em>t </em>hours. For example, if <em>P</em>(0) doubles in 3 hours, then <em>P</em>(3) = 2<em>P</em>(0).

Use the examples we worked out in lecture 9 and in the reading handout to write your unit tests. Save your code in hw05.py

After find_growth_model works to your satisfaction, use it to solve the following problem.

A bacteria culture that exhibits exponential growth quadruples in size in 2 days. If the initial size of the culture is 20,000, what is its size after 12 hours?

<h1>Problem 3: Radioactive Decay</h1>

Write a function radioactive_decay(lmbda, p0, t) that takes three constants and determines decay models for various radioactive materials. Specifically, it returns a function representation of the decay model for a material described by the given parameters, where lmbda specifies <em>λ</em>, p0 – the initial amount of radioactive material in grams, and <em>t </em>– a number of years. You may assume that each material is modeled with <em>P</em>(<em>t</em>) = <em>P</em>(0)<em>e</em><sup>−<em>λt</em></sup>, where <em>P</em>(0) = p0.

Use the examples we worked out in lecture 10 and in the reading handout to write your unit tests. Save your code in hw05.py.

After radioactive_decay works to your satisfaction, use it to solve the following problem.

A sample of 8 grams of radioactive material is placed in a vault. If <em>λ </em>= 0<em>.</em>021, how much of the material will remain in the vault after 10 years?

<h1>Problem 4: Carbon Dating</h1>

Write a function c14_carbon_dating(c14_percentage) that takes a constant describing the percentage of <sup>14</sup>C found in an object and returns an approximate age of the object according to the carbon dating model. The object’s age is a constant whose float value is rounded up with math.ceil.

Use the examples we worked out in lecture 10 and in the reading handout to write your unit tests. Save your code in hw05.py.

After c14_carbon_dating(c14_percentage) works to your satisfaction, use it to solve the following two problems.

<strong>Problem A: </strong>In 1947, a cave with beautiful prehistoric wall paintings was discovered in Lascaux, France. Some charcoal found in the cave contained 20% of <sup>14</sup>C expected in living trees. How old are the Lascaux cave paintings?

<strong>Problem B: </strong>A wooden chest was found in the tomb of the 25th century B.C. Chaldean king Meskalumdug of Ur. The chest contained 58.3% of <sup>14</sup>C expected in living trees. How old is the chest?

<h1>Problem 5: Elasticity of Demand</h1>

Write a function demand_elasticity(demand_eq, price) that takes a function representation of a demand equation (as a function of price <em>p</em>) and a price constant and returns a constant whose float value describes the elasticity of demand at the specified price.

Write a boolean function is_demand_elastic(demand_eq, price) that takes a function representation of a demand equation (as a function of price <em>p</em>) and a price constant and returns True if demand is elastic at the specified price and False otherwise.

Write a boolean function expected_rev_dir(demand_eq, price, price_dir) that takes a function representation of a demand equation (as a function of price <em>p</em>), a price constant, and a price direction constant (i.e., +1 – the price will be increased; -1 – the price will be lowered) and returns a constant that specifies the expected direction of revenue after the price action is taken (i.e., +1 – revenue will go up; -1 – revenue will go down).

Use the examples we worked out in lecture 10 and in the reading handout to write your unit tests. Save your code in hw05.py.

After these functions work to your satisfaction, use them to solve the following problem.

The number of people attending a show in a movie theater at a price of <em>p </em>dollars per ticket is <em>q </em>= (18<em>,</em>000<em>/p</em>)−1500. Is demand elastic at <em>p </em>= $6? If the price is lowered, will revenue increase or decrease