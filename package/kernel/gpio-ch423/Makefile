include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=gpio-ch423
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_LICENSE:=GPL-2.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/frank-zago/ch423-gpio-expander.git
PKG_SOURCE_VERSION:=5be33580b9690187196dc1e7be37164b2abd6090

include $(INCLUDE_DIR)/package.mk

define KernelPackage/gpio-ch423
  SECTION:=kernel
  SUBMENU:=GPIO support
  TITLE:=CH423 I2C GPIO expander
  DEPENDS:=@GPIO_SUPPORT +kmod-i2c-core
  FILES:=$(PKG_BUILD_DIR)/ch423.ko
  AUTOLOAD:=$(call AutoLoad,80,ch423)
endef

define KernelPackage/gpio-ch423/description
  Kernel module for WinChipHead CH423, a GPIO expander driver
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define Build/Compile
	$(KERNEL_MAKE) M="$(PKG_BUILD_DIR)" modules
endef

$(eval $(call KernelPackage,gpio-ch423))
