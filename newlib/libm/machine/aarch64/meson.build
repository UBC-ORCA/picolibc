#
# SPDX-License-Identifier: BSD-3-Clause
#
# Copyright © 2019 Keith Packard
# Copyright © 2020 Anthony Anderson
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

srcs_libm_machine_real = [
  'e_sqrt.c',
  'ef_sqrt.c',
  'fenv.c',
  's_ceil.c',
  's_fabs.c',
  's_floor.c',
  's_fma.c',
  's_fmax.c',
  's_fmin.c',
  's_llrint.c',
  's_llround.c',
  's_lrint.c',
  's_lround.c',
  's_trunc.c',
  'sf_ceil.c',
  'sf_fabs.c',
  'sf_floor.c',
  'sf_fma.c',
  'sf_fmax.c',
  'sf_fmin.c',
  'sf_llrint.c',
  'sf_llround.c',
  'sf_lrint.c',
  'sf_lround.c',
  'sf_nearbyint.c',
  'sf_rint.c',
  'sf_round.c',
  'sf_trunc.c'
]

srcs_libm_machine = srcs_libm_machine_real + [
  'feclearexcept.c',
  'fedisableexcept.c',
  'feenableexcept.c',
  'fegetenv.c',
  'fegetexcept.c',
  'fegetexceptflag.c',
  'fegetround.c',
  'feholdexcept.c',
  'feraiseexcept.c',
  'fesetenv.c',
  'fesetexceptflag.c',
  'fesetround.c',
  'fetestexcept.c',
  'feupdateenv.c',
]

src_libm_machine = files(srcs_libm_machine_real)
