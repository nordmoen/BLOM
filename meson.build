project('blom', ['fortran', 'c'], version: '0.1.0')

# Define global dependencies that multiple subdirectories will utilize
omp = dependency('openmp', required: false)

# Include directories with header files
phy_inc = include_directories('phy')
trc_inc = include_directories('trc')

# Process the following subdirectories which contain other 'meson.build' files
subdir('phy')
