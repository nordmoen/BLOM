dimensions = library('dimensions', 'dimensions.F')

wtime = library('wtime', 'wtime.F')

mod_xc = library('mod_xc', ['mod_xc.F'],
  link_with: [dimensions, wtime],
  extra_files: ['mod_xc_mp.inc', 'mod_xc_sm.inc'],
  dependencies: [omp])

crc = library('crc', 'crc.c',
  include_directories: [phy_inc])

chksum = library('chksum', 'chksum.F',
  link_with: [mod_xc, crc])

chksummsk = library('chksummsk', 'chksummsk.F',
  link_with: [mod_xc, crc])

triint = library('triint', 'triint.F')

penint = library('penint', 'penint.F')

remap_eitflx = library('remap_eitflx', 'remap_eitflx.F',
  include_directories: [trc_inc],
  link_with: [mod_xc, triint, penint])

remap_eitvel = library('remap_eitvel', 'remap_eitvel.F',
  include_directories: [trc_inc],
  link_with: [mod_xc, triint, penint])

advect = library('advect', 'advect.F',
  link_with: [mod_xc, chksummsk, remap_eitflx, remap_eitvel],
  include_directories: [phy_inc, trc_inc],
  dependencies: [omp])
