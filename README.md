# dma_uvm
UVM verification of a configurable AXI4 DMA able to transfer memory blocks → memory, with burst, interrupt, and error handling.


## axidma design
Here I chose to use the design from [ZipCPU/wb2axip git repo](https://github.com/ZipCPU/wb2axip)

The [AXIDMA](rtl/axidma.v) is a hardware assisted memory copy.  Given a source
  address, read address, and length, this core reads from the source address
  into a FIFO, and then writes the data from the FIFO to memory.  As an
  optimization, memory address requests are not made unless the core is able
  to transfer at a 100% throughput rate.