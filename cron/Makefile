#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Original patches ported from Optware
#

include $(TOPDIR)/rules.mk

PKG_NAME:=cron
PKG_VERSION:=4.1
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).shar
PKG_SOURCE_URL:=ftp://ftp.isc.org/isc/cron
PKG_MD5SUM:=5e1be9dbde66295821ac7899f2e1f561

include $(INCLUDE_DIR)/package.mk

PKG_UNPACK=cd $(PKG_BUILD_DIR) && cat $(DL_DIR)/$(PKG_SOURCE) | sh -x

define Package/cron
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Vixie cron
	URL:=ftp://ftp.isc.org/isc/cron
	MAINTAINER:=Entware team, old.entware.net
endef

define Package/cron/description
 Standart Vixie cron, with cron.d addition.
endef

define Package/cron/conffiles
/opt/etc/crontab
endef

define Package/cron/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/crontab $(1)/opt/bin
	$(INSTALL_BIN) ./files/run-parts $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/cron $(1)/opt/sbin
	$(INSTALL_DIR) $(1)/opt/etc/cron.d
	$(INSTALL_CONF) ./files/crontab $(1)/opt/etc
	$(INSTALL_DIR) \
		$(1)/opt/var/run \
		$(1)/opt/var/cron/crontabs \
		$(1)/opt/etc/cron.{1min,5mins,hourly,daily,weekly,monthly}
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S10cron $(1)/opt/etc/init.d/
endef

$(eval $(call BuildPackage,cron))
