Week 5 Half B Report

My UVM library did not compile because the location was a read only, and it still didn't work compiling outside it.

1. finish_item is blocked until the driver calls item_done, so transaction results are seen before choosing 
the next: retry, escalate, or stop. put() returns immediately, so my generator queued items blind.

2. If two hundred tests sharing one environment, every variation needs its own compile, so N snapshots, 
N compile times, and N chances fro the environment to drift. A factory override is a runtime decision 
in one compiled environment, so every other test runs the unchanged environment.

3. If the driver is a class four levels down in a hierarchy someone else wrote, every 
intermediate class accepts the virtual interface and passes it down, which means editing 
other's code every time you handle something new. uvm_config_db sets the handle once and 
the driver retrieves it by name in its own build phase without intermediate layers caring.
