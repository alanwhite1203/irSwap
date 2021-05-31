# Interest Rate Swap Valuation Practical Guide

Overview
An interest rate swap is an agreement between two parties to exchange future interest rate payments over a set period of time. It consists of a series of payment periods, called swaplets. The most popular form of interest rate swaps is the vanilla swaps that involve the exchange of a fixed interest rate for a floating rate, or vice versa. There are two legs associated with each party: a fixed leg and a floating leg. Swaps are OTC derivatives that bear counterparty credit risk beside interest rate risk. 
Interest rate swaps are the most popular OTC derivatives that are generally used to manage exposure to fluctuations in interest rates. Swaps can be also used to obtain a marginally lower interest rate. Thus they are often utilized by a firm that can borrow money easily at one type of interest rate but prefers a different type. They also allow investors to adjust interest rate exposure and offset interest rate risks. Speculators use swaps to speculate on the movement of interest rates. More and more swaps are cleared through central counterparties nowadays (CCPs). This presentation gives an overview of interest rate swap product and valuation model. 

	Keywords
Interest rate swap, OTC derivatives, swaplet, valuation, pricing model, interest rate risk

	Interest Rate Swap Introduction
	An interest rate swap is an agreement between two parties to exchange future interest rate payments over a set period of time.
	Vanilla Interest Rate Swaps involve the exchange of a fixed interest rate for a floating rate, or vice versa.
	There are two legs associated with each party: a fixed leg and a floating leg.
	Swaps are OTC derivatives that bear counterparty credit risk beside interest rate risk.
	An interest rate swap consists of a series of payment periods, called swaplets.

	The Use of Interest Rate Swap 
	Swaps are the most popular OTC derivatives that are generally used to manage exposure to fluctuations in interest rates.
	Swaps can be also used to obtain a marginally lower interest rate. Thus they are often utilized by a firm that can borrow money easily at one type of interest rate but prefers a different type.
	Swaps allow investors to adjust interest rate exposure and offset interest rate risks.
	Speculators use swaps to speculate on the movement of interest rates.
	More and more swaps are cleared through central counterparties nowadays (CCPs)


	Swap or Swaplet Payoff
	From the fixed rate payer perspective, the payoff of a swap or swaplet at payment date T is given by
〖Payff〗_payer=Nτ(R-F)
where 
N- the notional;
 τ – accrual period in years (e.g., a 3 month period ≈ 3/12 = 0.25)
R – the fixed rate in simply compounding.
F – the realized floating rate in simply compounding
	From the fixed rate receiver perspective, the payoff of a swap or swaplet at payment date T is given by
〖Payff〗_receiver=Nτ(F-R)

	Valuation
	The present value of a fixed rate leg is given by

〖PV〗_fixed (t)=RN∑_(i=1)^n▒〖τ_i D_i 〗
where t is the valuation date and D_i=D(t,T_i) is the discount factor.
	The present value of a floating leg is given by
〖PV〗_float (t)=N∑_(i=1)^n▒〖(F_i+s) τ_i D_i 〗
where F_i=(D_(i-1)/D_i -1)/τ_i is the simply compounded forward rate and s is the floating spread.
	The present value of an interest rate swap can expressed as
	From the fixed rate payer perspective, PV=〖PV〗_float-〖PV〗_fixed		
	From the fixed rate receiver perspective, PV=〖PV〗_fixed-〖PV〗_float

	Practical Notes
	First of all, you need to generate accurate cash flows for each leg. The cash flow generation is based on the start time, end time and payment frequency of the leg, plus calendar (holidays), business convention (e.g., modified following, following, etc.) and whether sticky month end.
	We assume that accrual periods are the same as reset periods and payment dates are the same as accrual end dates in the above formulas for brevity. But in fact, they are different due to different market conventions. For example, index periods can overlap each other but swap cash flows are not allowed to overlap.
	The accrual period is calculated according to the start date and end date of a cash flow plus day count convention 
	The forward rate should be computed based on the reset period (index reset date, index start date, index end date)  that are determined by index definition, such as index tenor and convention. it is simply compounded.
	Sometimes there is a floating spread added on the top of the floating rate in the floating leg.
	The formula above doesn’t contain the last live reset cash flow whose reset date is less than valuation date but payment date is greater than valuation date. The reset value is
〖PV〗_reset=r_0 Nτ_0 D_0  
where r_0 is the reset rate. 
	The present value of the reset cash flow should be added into the present value of the floating leg.
	Some dealers take bid-offer spreads into account. In this case, one should use bid curve constructed from bid quotes for forwarding and offer curve built from offer quotes for discounting.

	A Real World Example
Leg 1 Specification	Leg 2 Specification
Currency	USD	Currency	USD
Day Count	dcAct360	Day Count	dcAct360
Leg Type	Fixed	Leg Type	Float
Notional	5000000	Notional	5000000
Pay Receive	Receive	Pay Receive	Pay
Payment Frequency	1M	Payment Frequency	1M
Start Date	7/1/2015	Start Date	7/1/2015
End Date	3/1/2023	End Date	3/1/2023
Fixed Rate	0.0455	Spread	0
		Index Specification
		Index Type	LIBOR
		Index Tenor	1M
		Index Day Count	dcAct360


References:

https://finpricing.com/lib/EqVariance.html

https://bitbucket.org/cmrm11/irswap/downloads/IrSwap-36.pdf

