#
# SPDX-License-Identifier: BSD-3-Clause
#
# Copyright © 2019 Keith Packard
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer.
#
# 2. Redistributions in binary form must reproduce the above
#    copyright notice, this list of conditions and the following
#    disclaimer in the documentation and/or other materials provided
#    with the distribution.
#
# 3. Neither the name of the copyright holder nor the names of its
#    contributors may be used to endorse or promote products derived
#    from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
# FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE
# COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT,
# INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
# (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
# SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
# HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT,
# STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED
# OF THE POSSIBILITY OF SUCH DAMAGE.
#

src_picocrt = []

machine_dir = 'machine' / host_cpu_family
if fs.is_dir(machine_dir)
  subdir(machine_dir)
else
  src_picocrt = files('shared/crt0.c')
endif

foreach target : targets
  value = get_variable('target_' + target)

  instdir = join_paths(get_option('libdir'), value[0])

  if target == ''
    crt_name = 'crt0.o'
    crt_hosted_name = 'crt0-hosted.o'
    crt_minimal_name = 'crt0-minimal.o'
    libcrt_name = 'crt'
    libcrt_hosted_name = 'crt-hosted'
    libcrt_minimal_name = 'crt-minimal'
  else
    crt_name = join_paths(target, 'crt0.o')
    crt_hosted_name = join_paths(target, 'crt0-hosted.o')
    crt_minimal_name = join_paths(target, 'crt0-minimal.o')
    libcrt_name = join_paths(target, 'libcrt')
    libcrt_hosted_name = join_paths(target, 'libcrt-hosted')
    libcrt_minimal_name = join_paths(target, 'libcrt-minimal')
  endif

  # The normal variant does not call 'exit' after return from main (c lingo: freestanding execution environment)
  executable(crt_name,
	     src_picocrt,
	     include_directories : inc,
	     install : true,
	     install_dir : instdir,
	     c_args : value[1] + arg_fnobuiltin + ['-ffreestanding'],
	     link_args : value[1] + ['-r', '-ffreestanding', '-nostdlib'])

  # Tests link against this because using the .o isn't supported under meson
  set_variable('lib_crt' + target,
	       static_library(libcrt_name,
			      src_picocrt,
			      install : false,
			      include_directories : inc,
			      c_args : value[1]))

  # The 'hosted' variant calls 'exit' after return from main (c lingo: hosted execution environment)
  executable(crt_hosted_name,
             src_picocrt,
             include_directories : inc,
             install : true,
             install_dir : instdir,
             c_args : value[1] + arg_fnobuiltin + ['-ffreestanding', '-DCRT0_EXIT'],
             link_args : value[1] + ['-r', '-ffreestanding', '-nostdlib'])

  # Tests link against this because using the .o isn't supported under meson
  set_variable('lib_crt_hosted' + target,
	       static_library(libcrt_hosted_name,
			      src_picocrt,
			      install : false,
			      include_directories : inc,
			      c_args : value[1] + ['-DCRT0_EXIT']))

  # The 'minimal' variant doesn't call exit, nor does it invoke any constructors
  executable(crt_minimal_name,
             src_picocrt,
             include_directories : inc,
             install : true,
             install_dir : instdir,
             c_args : value[1] + arg_fnobuiltin + ['-ffreestanding', '-DCONSTRUCTORS=0'],
             link_args : value[1] + ['-r', '-ffreestanding', '-nostdlib'])

  # Tests link against this because using the .o isn't supported under meson
  set_variable('lib_crt_minimal' + target,
	       static_library(libcrt_minimal_name,
			      src_picocrt,
			      install : false,
			      include_directories : inc,
			      c_args : value[1] + ['-DCONSTRUCTORS=0']))
endforeach
