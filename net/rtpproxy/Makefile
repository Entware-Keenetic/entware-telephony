#
# Copyright (C) 2014 OpenWrt.org
# Copyright (C) 2017 Jiri Slachta <jiri@slachta.eu>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rtpproxy
PKG_VERSION:=2.0.0
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sippy/rtpproxy.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=d5926892630139bcbe55d1f3fa36764c881648bc
PKG_MIRROR_HASH:=7da4a9b83f01b4169cf3f087c76e73fd9b4f5afb8d543c4663e874d8d9b1b26a
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_CHECK_FORMAT_SECURITY:=0
PKG_INSTALL:=1

PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Jiri Slachta <jiri@slachta.eu>

include $(INCLUDE_DIR)/package.mk

define Package/rtpproxy
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Telephony
  DEPENDS:=+libpthread +librt
  TITLE:=RTP (Realtime Transport Protocol) proxy
  URL:=http://www.rtpproxy.org/
endef

CONFIGURE_VARS += \
        ac_cv_lib_bcg729_initBcg729EncoderChannel=no

define Package/rtpproxy/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/rtpproxy $(1)/opt/bin/

	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S18rtpproxy $(1)/opt/etc/init.d
endef

$(eval $(call BuildPackage,rtpproxy))
