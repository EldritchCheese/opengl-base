# -*- python -*-

import os
from os.path import join as pjoin

Import('env')

libs = []

# custom engine
env.Append(CPPPATH=['#/engine/include'])
libNGine = env.SConscript('engine/SConscript',exports=['env'])
libs.append(libNGine)

# assimp
if env['CPPDEFINES'] and ('USE_ASSIMP_LIBRARY' in env['CPPDEFINES']):
    env.Append(CPPPATH=['#/ext_libs/assimp-3.0.1270/include'])
    env.Append(LIBS=['z'])
    libASSIMP = env.SConscript('ext_libs/assimp-3.0.1270/SConscript',exports=['env'])
    libs.append(libASSIMP)

# GLFW
libGLFW = env.SConscript('ext_libs/glfw-3.0.4/SConscript',exports=['env'])
libs.append(libGLFW)
env.Append(CPPPATH=['#/ext_libs/glfw-3.0.4/include'])

# GLEW
env.Append(CPPDEFINES=['GLEW_STATIC'])
libGLEW = env.SConscript('ext_libs/glew-1.10.0/SConscript',exports=['env'])
libs.append(libGLEW)
env.Append(CPPPATH=['#/ext_libs/glew-1.10.0/include'])

# SOIL
env.Append(CPPPATH=['#/ext_libs/soil'])
libSOIL = env.SConscript('ext_libs/soil/SConscript',exports=['env'])
libs.append(libSOIL)

# GL
env.Append(LIBS=['$OPENGL'])

# GLM
env.Append(CPPPATH=['#/ext_libs/glm-0.9.5.3'])
env.Append(CCFLAGS=['-DGLM_FORCE_RADIANS'])

env.Append(RPATH=[Literal('\\$$ORIGIN')])
env.Append(CPPPATH=['#/include'])

exe = env.Program(['Program.cc',Glob('src/*.cc'),libs])

Return('exe')
