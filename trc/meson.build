trc_srcs = ['initrc.F', 'ocntrc_init.F', 'restart_ocntrcrd.F',
'restart_ocntrcwt.F', 'restart_trcrd.F', 'restart_trcwt.F', 'updtrc.F']

if get_option('trc')
  foreach src: trc_srcs
    sources += 'trc/' + src
  endforeach
endif
