# OpenWrt package for the Vallia Agent.
#
# EXPERIMENTAL / ADVANCED. Building this needs the OpenWrt SDK, and scapy +
# python3 are heavy for many home routers (flash/RAM). For most users the
# Docker or Raspberry Pi route is recommended — see the main README.
#
# Build (inside an OpenWrt SDK tree):
#   1) cp ../vallia_agent.py ./files/vallia_agent.py
#   2) place this folder under package/vallia-agent/
#   3) make package/vallia-agent/compile V=s
#
include $(TOPDIR)/rules.mk

PKG_NAME:=vallia-agent
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/vallia-agent
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Vallia Agent (LAN sensor for the Vallia app)
  URL:=https://github.com/gigix21288/Vallia-Agent
  DEPENDS:=+python3-light +python3-asyncio +python3-logging +libpcap
endef

define Package/vallia-agent/description
  Streams LAN packet headers to the Vallia phone app over a local
  WebSocket. Requires python3-scapy and python3-websockets to be installed via
  pip on the device (not in the OpenWrt feeds). Experimental.
endef

define Build/Compile
endef

define Package/vallia-agent/install
	$(INSTALL_DIR) $(1)/opt/vallia-agent
	$(INSTALL_BIN) ./files/vallia_agent.py $(1)/opt/vallia-agent/vallia_agent.py
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/vallia-agent.init $(1)/etc/init.d/vallia-agent
endef

$(eval $(call BuildPackage,vallia-agent))
