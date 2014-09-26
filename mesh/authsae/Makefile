# Copyright (C) Thomas Wagner Thomas.Wagner@hs-rm.de
# based on http://patchwork.openwrt.org/patch/1350/
#
# This is free software, licensed under the GNU General Public License v2.

include $(TOPDIR)/rules.mk

PKG_NAME:=authsae
PKG_VERSION:=bd8048e
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/authsae
  SECTION:=net
  CATEGORY:=Network
  TITLE:=o11s mesh security
  DEPENDS=+libopenssl +libconfig +libnl
endef

TARGET_CFLAGS += -D_GNU_SOURCE

define Package/authsae/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/build/linux/mon \
                       $(PKG_BUILD_DIR)/build/linux/meshd \
                       $(PKG_BUILD_DIR)/build/linux/meshd-nl80211 $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/config/authsae.sample.cfg $(1)/etc/authsae.cfg
endef

define Package/conffiles
	/etc/authsae.cfg
endef

define Build/Prepare
	echo $(PKG_BUILD_DIR)
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) -r ./src/* $(PKG_BUILD_DIR)/
endef

define Build/compile
	echo compile
	$(MAKE) -C $(PKG_BUILD_DIR)/linux
endef

$(eval $(call BuildPackage,authsae))
