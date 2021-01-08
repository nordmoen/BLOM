project('BLOM', ['fortran', 'c'],
  version: '0.1.0',
  meson_version: '>= 0.54.0',
  default_options: ['warning_level=2'])

# Setup additional flags for compilation
fcc = meson.get_compiler('fortran')
if fcc.get_id() == 'gcc'
  add_global_arguments(['-fdefault-real-8'], language: 'fortran')
else
  warning('Unknown Fortran compiler ("' + fcc.get_id() + '"), no default flags specified')
endif

# Handle options and add necessary flags
if get_option('levitus2x')
  add_global_arguments('-DLEVITUS2X', language: 'fortran')
endif

# Define global dependencies that multiple subdirectories will utilize
netcdf = dependency('netcdf', language: 'fortran')
omp = dependency('openmp', required: false)
quadmath = fcc.find_library('quadmath')

# Include directories with header files
cesm_inc = include_directories('cesm')
phy_inc = include_directories('phy')
trc_inc = include_directories('trc')

# List of all sources in the project
sources = []

# Process the following subdirectories which contain other 'meson.build' files
# that will fill out 'sources'
subdir('ben02')
subdir('cesm')
subdir('drivers')
subdir('phy')

# Create BLOM executable
executable('blom', sources,
  include_directories: [cesm_inc, phy_inc, trc_inc],
  dependencies: [netcdf, omp, quadmath])
