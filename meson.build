project('decNumber', 'c', version: '3.68')
add_project_arguments('-DDECNUMDIGITS=62', '-DDECPRINT=0', '-DDECLITEND=1', '-D_CRT_SECURE_NO_WARNINGS', language : 'c')
static_library('decNumber', 
	'decNumber/decContext.c',
  'decNumber/decDouble.c',
  'decNumber/decNumber.c',
  'decNumber/decPacked.c',
  'decNumber/decQuad.c',
  'decNumber/decSingle.c')
