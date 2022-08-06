# gnumeric-options-plugin
Minor customizations to the gnumeric fn-derivatives plugin

This includes a few minor customizations to the options plugin in gnumeric.

The optional cost-of-carry parameter in spreadsheet functions such as opt_bs (Generalized Black-Scholes model) or opt_binomial is set by default to be zero in gnumeric. This leads to some possibly unexpected results. For example, opt_bs would by default give the Black model price of an option on a futures contract, rather than the Black-Scholes model price of an option on a share. I changed this default to equal the risk-free rate, so that now opt_bs and related functions refer to the price of an option on a share. This changed default is in the following functions:

opt_bs (generalized Black-Scholes)
opt_bs_delta (Black-Scholes delta)
opt_bs_gamma (Black-Scholes gamma)
opt_bs_theta (Black-Scholes theta)
opt_bs_vega (Black-Scholes vega)
opt_bs_rho (Black-Scholes rho)
opt_bs_carrycost (Black Scholes carry)

The default is also changed for the binomial model. In addition, I changed the name of the binomial function from opt_binomial to opt_binomial_crr (to reflect that it applies the Cox-Ross-Rubinstein or CRR model). 

I added an additional function opt_binomial_eqprob, that applies the equal probabilities binomial model to value options.

I also added a few convenience functions: opt_bs_call to find the Black-Scholes value of a call, and opt_bs_put to find the Black-Scholes value of a put. 

To apply these customizations:

Copy the files "options.c" and "plugin.xml.in" in this repository to the "plugins/fn-derivatives" directory in your gnumeric source (you may wish to back up the original versions), then recompile your gnumeric.









