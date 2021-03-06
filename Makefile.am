
# Copyright © 2013 Intel Corporation
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice (including the next
# paragraph) shall be included in all copies or substantial portions of the
# Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.

SUBDIRS = include/epoxy src

SUBDIRS += test

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = epoxy.pc

registry_files = \
	registry/egl.xml \
	registry/gl.xml \
	registry/glx.xml \
	registry/wgl.xml \
	$()

meson_build_files = \
	meson_options.txt \
	meson.build \
	include/epoxy/meson.build \
	src/meson.build \
	test/meson.build \
	doc/meson.build \
	doc/Doxyfile.in \
	cross/fedora-mingw64.txt \
	$()

EXTRA_DIST = \
	.dir-locals.el \
	README.md \
	autogen.sh \
	epoxy.pc.in \
	$(registry_files) \
	$(meson_build_files) \
	$()

dist-hook:
	@if test -d "$(top_srcdir)/.git"; then \
	  echo Generating ChangeLog... ; \
	  ( $(top_srcdir)/missing --run git log --stat ) > "$(top_srcdir)/ChangeLog.tmp" \
	  && mv -f "$(top_srcdir)/ChangeLog.tmp" "$(top_distdir)/ChangeLog" \
	  || ( rm -f "$(top_srcdir)/ChangeLog.tmp"; \
	       echo Failed to generate ChangeLog >&2 ); \
	else \
	  echo A git checkout is required to generate a ChangeLog >&2; \
	fi
