# RDMA
RDMA Processing code


nimbus must be run first to produce a netCDF file and corresponding '.cnts.rdma'
text file.  Run rdmap which all ask for the name of the '.cnts.rdma' file.
This file has a pointer back to the netCDF file.  Pressure and temperature
(PSXC & ATX) are read from the netCDF file.  Processor loops over the 'counts'
records from the text file.  A new set of matrix co-efficients and cell diameters
are generated for the given pressure/temperature (rmda_mat.cc).  Then the
inversion (rdma_inv.cc) is called with the 'counts' array, the matrix co-efficients
and the new diameters.  This produces concentrations, which are then stuffed
back into the netCDF file by rdmap.

rdma_mat.cc and rdma_inv.cc are source files that came with the RDMA.  I have
modified them so that they can be called by the wrapper program I wrote rdmap.cc.
rmda_mat.cc and rdma_inv.cc produce many text files, these can be found in
${DATA_DIR}/rdma/dma/inv/[input|output].


The *orginal* directory has some of the original code that was given to me
to work with.
