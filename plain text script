import math as math
import numpy as np
import scipy.stats as si
import sympy as sy
from sympy.stats import Normal, cdf

a = int(input("Enter the current stock price:"))
b = int(input("Enter the strike price:"))
c = float(input("Enter the time until option exercise:"))
d = float(input("Enter the risk-free rate, or the T-Bill rate:"))
e = float(input("Enter the implied volatility:"))
f = input("Enter where the option is a call or put:")

def european_option(S, X, t, r, o, option = 'call' or 'put'):

#S represents the current stock price
#X represents the strike price
#t represents the time until the option exercise
#r represents the risk-free rate, or the T-Bill rate
#o represents the implied volatility
    
    d1CP = (np.log(S/X,out=None,where=True,casting='same_kind',order='K',dtype=None) + ((r+(o ** 2))/2) * t) / (o*np.sqrt(t))
    d2CP = (np.log(S/X, out=None,where=True,casting='same_kind',order='K',dtype=None) + ((r-(o ** 2))/2) * t) / (o*np.sqrt(t))

    if option == 'call':
        result = (S*si.norm.cdf(d1CP,0,1) - X*np.exp(-r*t)*si.norm.cdf(d2CP,0,1))
        delta = math.exp(-r*t)*si.norm.cdf(d1CP,0,1)
        gamma = ((1/np.sqrt(2*3.14159))*(math.exp((-d1CP)**2/2))*(math.exp(-r*t)))/(S*o*np.sqrt(t))
        
    if option == 'put':
        result = (X*np.exp(-r*t)*si.norm.cdf(-d2CP,0,1) - S*si.norm.cdf(-d1CP,0,1));
        delta = -math.exp(-r*t)*si.norm.cdf(-d1CP,0,1)
        gamma = ((1/np.sqrt(2*3.14159))*(math.exp((-d1CP)**2/2))*(math.exp(-r*t)))/(S*o*np.sqrt(t))     

    return result, delta, gamma

print("The option value, delta and gamma for this", f,"is: (respectively)")
print(european_option(a, b, c, d, e, option = f)) 
