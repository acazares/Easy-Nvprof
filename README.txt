===========
easy-nvprof
===========

easy-nvprof is a schell script that wraps around 
nvprof in order to add other options. By other options, 
I am referring to options that will either print a
group of metrics or events without having to type every 
single event and metric that one may want. This can be 
useful when profiling cuda code and with no access to 
the cuda visual profiler. The way it works is pretty 
simple. getpot is used to check if any options that
it expects were given on the command line and if an 
option was given the appropriate operation is done 
for that option. "easy-nvprof" can be given metrics 
and events and can also print the list of metrics and 
events just like nvprof. In the script there are 
variables for metrics and events and as the list of
options that getopt found are processed, the 
appropriate metrics and events are added to the
variables. In the end, one single call is made to
nvprof.   
  

========
Versions
========

	Version 1
	=========
	
	This version has the options utilization and
	efficiency. Utilization adds all the metrics
	that are used to check the utilization of
	cuda code to the metrics variables. The 
	efficiency option does the same only adds the 
	efficiency metrics. The utilization can be given
	two options which are mem and comp. If mem is 
	given, the metrics that concern memory 
	utilization are added to the variable and if comp
	is given the metrics that concern computational
	utilization are added to the the variable. As
	for efficiency, this can be given four options
	which are gmem, smem, tcomp and wcomp. gmem are
	metrics that concern global memory efficiency, 
	smem is shared memory efficiency, tcomp is 
	computation efficiency at the thread level and
	wcomp is computation efficiency at the warp
	level. If no options are given to utilization
	and efficiency, they will print all the metrics
	that their options produce. This effect can 
	also be done by giving the option 'all'. 
	Also don't forget individual metrics and events 
	can be given in the same manner that they are 
	given to nvprof.  


========
Examples
========

easy-nvprof --utilization=mem [program]
easy-nvprof --u=comp --efficiency=gmem [program]
easy-nvprof --u=mem --e=all --metrics achieved_occupancy [program]
