# Purpose of this repository
In this repository, two load patterns are described Sinusoid and FlashCrowd. They were written in Python for experiments involving video clients (eg. VLC) consuming video services (eg. DASH).

# Sinusoid

 The Sinusoid load generator produces requests following a Poisson process whose arrival rate is modulated by a function, where: A represents an amplitude; F the frequency; and \lambda is a phase in radians. 

$$ f(y) = A \sin(F + \lambda)

