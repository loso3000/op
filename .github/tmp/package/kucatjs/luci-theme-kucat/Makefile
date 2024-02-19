#
# Copyright (C) 2019-2024 The Sirpdboy Team <herboy2008@gmail.com>    
#
# This is free software, licensed under the Apache License, Version 2.0 .
#

include $(TOPDIR)/rules.mk
THEME_NAME:=kucat
THEME_TITLE:=Kucat Theme
PKG_NAME:=luci-theme-$(THEME_NAME)
LUCI_TITLE:=Kucat Theme by sirpdboy
LUCI_DEPENDS:=
PKG_VERSION:=2.3.10
PKG_RELEASE:=20240219

include $(INCLUDE_DIR)/package.mk

define Package/luci-theme-$(THEME_NAME)
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=9. Themes
  DEPENDS:=+libc
  TITLE:=LuCi Theme For OpenWrt $(THEME_NAME) Theme by sirpdboy
  URL:=http://www.ghithub.com/sirpdboy/luci-theme-$(THEME_NAME)/
  PKGARCH:=all
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/luci-theme-$(THEME_NAME)/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	echo "uci set luci.themes.$(THEME_TITLE)=/luci-static/$(THEME_NAME); uci commit luci" > $(1)/etc/uci-defaults/30-luci-theme-$(THEME_NAME)
	$(INSTALL_DIR) $(1)/www/luci-static/$(THEME_NAME)
	$(CP) -a ./luasrc/* $(1)/www/luci-static/$(THEME_NAME)/ 2>/dev/null || true
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/view/themes/$(THEME_NAME)
	$(CP) -a ./template/* $(1)/usr/lib/lua/luci/view/themes/$(THEME_NAME)/ 2>/dev/null || true
	$(INSTALL_DIR) $(1)/www/luci-static/resources
	$(CP) -a ./js/* $(1)/www/luci-static/resources/ 2>/dev/null || true
endef

define Package/luci-theme-$(THEME_NAME)/postinst
#!/bin/sh
[ -n "$${IPKG_INSTROOT}" ] || {
	( . /etc/uci-defaults/30-luci-theme-$(THEME_NAME) ) && rm -f /etc/uci-defaults/30-luci-theme-$(THEME_NAME)
}

rm -Rf /var/luci-modulecache
rm -Rf /var/luci-indexcache
exit 0
endef

$(eval $(call BuildPackage,luci-theme-$(THEME_NAME)))
