# Purpose of this repository
In this repository, two load patterns are described **Sinusoid** and **FlashCrowd**. They were written in Python for experiments involving video clients (eg. VLC) consuming video services (eg. DASH).

## Sinusoid

 The Sinusoid load generator produces requests following a Poisson process whose arrival rate is modulated by a function, where: A represents an amplitude; F the frequency; and \lambda is a phase in radians. 

$$ f(y) = A \sin(F + \lambda) $$

## Flashcrowd

The flashcrowd load describes a flash event, that is represented by a large spike or surge in traffic to a particular website. The flashcrowd is divided into three phases: **ramp-up**, **sustained** and **ramp-down**. 

Ramp-up is modeled by shock level (S), that is an order of magnitude increase in the average request (video clients) rate. Furthermore, it starts in $t_0$ and ends in $t_1$.

$$ rampup = \frac{1}{\log_{10}(1+ S)} $$

Sustained represents the maximum traffic (clients) level at the time interval $t_1$ and $t_2$. It is also modeled by $S$.

$$ sustained = \log_{10}(1+ S) $$

Ramp-down represents the end of the flash event, gradually decreasing the amount of traffic (video clients). In this phase, $n$ is a constant that defines the speed of reduction. Ramp-down is modeled by $n$ and $S$.

$$ rampdown = n\times \log_{10}(1+ S) $$


## Requirements
- Python 2.7
- VLC 

## Usage

### Sinusoid
```
usage: sinusoid.py [-h] [-V] [-v] [-s A,P] -l PLAYLIST [--poisson]
                   [--no-poisson]
                   duration lambd

positional arguments:
  duration              set the duration of the experiment in minutes
  lambd                 set the (average) arrival rate of lambda
                        clients/minute or normal level of functioning Rnorm
                        for flash crowd

optional arguments:
  -h, --help            show this help message and exit
  -V, --version         show program's version number and exit
  -v, --verbose         set verbosity level [default: None]
  -s A,P, --sinusoid A,P
                        set the sinusoidal lambda behavior, that varies with
                        amplitude A on period P minutes around the lambda
  -l PLAYLIST, --playlist PLAYLIST
                        Set the playlist for the clients
  --poisson
  --no-poisson
```
#### Flashcrowd