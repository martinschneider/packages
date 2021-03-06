# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2021 Martin Schneider <martschneider@google.com>

include $(TOPDIR)/rules.mk

PKG_NAME:=boringssl
PKG_VERSION:=20210608
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://boringssl.googlesource.com/boringssl
PKG_SOURCE_DATE:=2021-06-08
PKG_SOURCE_VERSION:=1f54fd9864c054dc33e15b1144e2a6a19fa0a52e
PKG_MIRROR_HASH:=a60c79ca40d1a73639d4c1bba3431ca630ab1d670ab06307e8442b69cfaf0cc7

PKG_MAINTAINER:=Martin Schneider <martschneider@google.com>\
	Bernie Innocenti <codewiz@google.com>
PKG_LICENSE:=OpenSSL,ISC
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/boringssl
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=An implementation of the TLS protocol
	URL:=https://boringssl.googlesource.com/boringssl/
	DEPENDS:=+golang \
		 @(i386||x86_64||arm||armeb||aarch64)
endef

define Package/boringssl/description
	An implementation of the TLS protocol
endef

define Package/boringssl/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/bin/libcrypto.a $(1)/usr/lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/bin/libssl.a $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/boringssl/lib
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/crypto/libcrypto.a $(1)/boringssl/lib/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/ssl/libssl.a $(1)/boringssl/lib/
	$(INSTALL_DIR) $(1)/boringssl/include/openssl
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/include/openssl/*.h $(1)/boringssl/include/openssl
endef

$(eval $(call BuildPackage,boringssl))
