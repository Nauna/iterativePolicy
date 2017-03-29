# iterativePolic


This question concerns a simplified model of inventory control with uncertain demand
for a certain stocked commodity. The commodity whose inventory is being controlled is assumed to be indivisible
(i.e., it occurs in integer quantities) and deterioration of stock is excluded (i.e., for simplicity, pilferage, spoilage, and
deterioration are assumed not to occur). Let xk denote the number of items on hand at the end of period k and let x0
be the number of items on hand initially. Assume that the number of items is limited by the integer M, i.e., at any
period no more thanM items can be in stock. The inventory level xk represents a state of the model. In each period,
the inventory control manager observes the inventory level and decides how many units, if any, to order. We assume
that delivery of replenishment items is instantaneous (i.e., items ordered from the supplier at the start of period k
become available at the beginning of period k + 1), and let ak be the amount ordered and delivered immediately.
Assume that no more than M − xk items can be ordered, if xk items are available in stock at the start of period k.
This means that in the state xk the only actions that can be executed are orders for 0, 1, . . . ,M−xk items. Let Dk be
demand for the item during period k. We assume that demands D1,D2, . . . ,Dk, . . . are independent and identically
distributed random variables following the given probability distribution Prob{Dk = d} = p(d) for 0  d  M,
i.e., for simplicity we assume that no more than M items can be demanded at any period k: PM
d=0 p(d) = 1. The
inventory on hand at the start of period k + 1 is determined by the equation
xk+1 =  0 if xk + ak − Dk+1  0,
xk + ak − Dk+1 if 0 < xk + ak − Dk+1  M.
In this equation, we assume that negative inventory levels xk are not allowed for any k (no backlogging); i.e., if
demand exceeds stock, then inventory has a shortage representing lost sales that cannot be filled by future orders. It
is easy to see, that if ak units ordered, then the probability of transition into the state with the inventory level 0 from
the state xk is equal to Pak
xk 0 = X dxk+ak
p(d), and the probability of transition to the state with the inventory level
0 < xk+1 < M from the state xk after ordering ak items is Pak
xk xk+1 = p(xk +ak −xk+1), if (xk +ak −xk+1)  0.
All other probabilities of transitions are 0, i.e., after doing the action ak in xk, the probability Pak
xk xk+1
of transition
from the state xk to the state xk+1 > (xk + ak) is 0 (this condition excludes negative demands). Note that all
probabilities are stationary, i.e., they do not depend on k.To describe the reward (cost) structure, we assume that the ordering cost C(ak), includes a (wholesale) unit
ordering cost c and a fixed delivery charge (or setup cost) K for placing any nonzero order (included in the setup
cost are the expenses of receiving the merchandise, putting the items received into inventory, etc). Consequently,
if at the start of period k the order ak > 0, then the total ordering cost C(ak) = c · ak + K, and if ak = 0, then
C(ak) = 0. In addition, there is an inventory holding cost of h for each item of remaining inventory at the end of a
period, and a penalty cost of z per unit of unsatisfied demand if the demand exceeds the present supply. Finally, we
assume that r is the (retail) unit sales price (assume that r > c). Consequently, if demand Dk+1 exceeds or is equal
to the present supply (xk +ak), then the revenue from sales is r · (xk +ak) and the expected penalty for unsatisfied
demand is z ·PM
d>(xk+ak)(d − xk − ak) · p(d). In this case, the one period expected income is
Rak
xk 0 = r · (xk + ak) − C(ak) − z ·
M
X d>(xk+ak)
(d − xk − ak) · p(d).
If the demand is less than the supply, Dk+1 < (xk + ak), then the one period expected income
Rak
xk xk+1 = r · (xk + ak − xk+1) − C(ak) − h · xk+1, where 0 < xk+1  xk + ak.
For all states xk+1 > (xk + ak), we define Rak
xk xk+1 = 0.
The objective is to maximize the total expected discounted income over an infinite time horizon when 
 is the
discount factor. Your task is to compute an optimal policy using algorithms introduced in class.
