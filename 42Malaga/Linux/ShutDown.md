Commands to gracefully shutdown Linux
Shut down gracefully and immediately
`$ shutdown -h now`

 

Shut down gracefully after X number of minutes
`$ shutdown -P +30 (P stands for Power Off)`
This will shut the machine down after 30 minutes. 

To shut down at a specific hour run;
`$ shutdown -P 3:00`
This will shut the machine down at 3:00 AM

 To cancel a pending/scheduled shutdown just do;
`$ shutdown -c`

