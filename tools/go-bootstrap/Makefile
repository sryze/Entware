#
# Copyright (C) 2016-2019 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=go-bootstrap
PKG_VERSION:=1.4.3
OS=$(shell uname | tr 'A-Z' 'a-z')
bintype:=$(shell uname -m | sed \
        -e 's/i[3-9]86/386/' \
        -e 's/x86_64/amd64/' \
)

PKG_HASH:=ce3140662f45356eb78bc16a88fc7cfb29fb00e18d7c632608245b789b2086d2
ifeq ($(OS),darwin)
  ifeq ($(bintype),arm64)
    PKG_VERSION:=1.16
    PKG_HASH:=4dac57c00168d30bbd02d95131d5de9ca88e04f2c5a29a404576f30ae9b54810
  endif
endif
PKG_SOURCE:=go$(PKG_VERSION).$(OS)-$(bintype).tar.gz
PKG_SOURCE_URL:=https://storage.googleapis.com/golang
HOST_BUILD_DIR:=$(STAGING_DIR_HOST)/go$(PKG_VERSION)
HOST_UNPACK:=gzip -dc $(DL_DIR)/$(PKG_SOURCE) | tar -C $(HOST_BUILD_DIR) --strip-components=1 -xf -

include $(INCLUDE_DIR)/host-build.mk

#build go for all architetures - in case gccgo does not work

define Host/Compile
endef

define Host/Install
endef

define Host/Clean
	rm -rf $(STAGING_DIR_HOST)/go1.4
endef

$(eval $(call HostBuild))
