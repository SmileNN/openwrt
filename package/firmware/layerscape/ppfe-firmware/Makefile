#
# Copyright (C) 2016 Jiang Yutang <jiangyutang1978@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ppfe
PKG_VERSION:=lf-6.1.1-1.0.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/nxp-qoriq/qoriq-engine-pfe-bin
PKG_SOURCE_VERSION:=lf-6.1.1-1.0.0
PKG_MIRROR_HASH:=59f5660f1b93314e3e073053195719eab7361f07d1a9e02896f9356b1a615873

PKG_FLAGS:=nonshared

include $(INCLUDE_DIR)/package.mk

RSTRIP:=:
STRIP:=:

define Package/layerscape-ppfe
  SECTION:=firmware
  CATEGORY:=Firmware
  TITLE:=NXP Layerscape PPFE firmware
  DEPENDS:=@TARGET_layerscape
  CONFIG_FW:=ls1012a/u-boot/pfe_fw_sbl.itb
  CONFIG_BIN1:=ls1012a/slow_path/ppfe_class_ls1012a.elf
  CONFIG_BIN2:=ls1012a/slow_path/ppfe_tmu_ls1012a.elf
  CONFIG_LIC:=NXP-Binary-EULA.txt
endef

define Build/Compile
endef

define Package/layerscape-ppfe/install
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/$(CONFIG_FW) \
		$(STAGING_DIR_IMAGE)/pfe.itb
	$(INSTALL_DIR) $(1)/lib/firmware/
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/$(CONFIG_BIN1) \
		$(PKG_BUILD_DIR)/$(CONFIG_BIN2) \
		$(PKG_BUILD_DIR)/$(CONFIG_LIC) \
		$(1)/lib/firmware/
endef

$(eval $(call BuildPackage,layerscape-ppfe))
