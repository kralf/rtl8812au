cmake_minimum_required(VERSION 2.6)

include(ReMake)

remake_project(
  rtl8812au
  VERSION 4.2.2
  RELEASE stable
  SUMMARY
    "Linux kernel driver for AC1200 (801.11ac) Wireless Dual-Band USB Adapter."
  AUTHOR "Realtek Semiconductor Corp."
  CONTACT "wlanfae@realtek.com"
  HOME "http://www.realtek.com.tw"
  LICENSE "GNU General Public License (GPL)"
  INSTALL /usr
)

remake_pack_deb(
  COMPONENT kernel-source
  DESCRIPTION "kernel module sources"
  DEPENDS dkms
  EXTRA debian/module/*
)
remake_pack_deb(
  DEPENDS rtl8812au-kernel-source
)

remake_distribute_deb(
  DISTRIBUTION lucid
  SECTION libs
  UPLOAD ppa:kralf/asl
  DEPENDS dkms remake
  PASS CMAKE_BUILD_TYPE RTL8812AU_GIT_REVISION
)
remake_distribute_deb(
  DISTRIBUTION precise
  SECTION libs
  UPLOAD ppa:kralf/asl
  DEPENDS dkms remake
  PASS CMAKE_BUILD_TYPE RTL8812AU_GIT_REVISION
)
remake_distribute_deb(
  DISTRIBUTION trusty
  SECTION libs
  UPLOAD ppa:kralf/asl
  DEPENDS dkms remake
  PASS CMAKE_BUILD_TYPE RTL8812AU_GIT_REVISION
)
