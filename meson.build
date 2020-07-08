# Copyright 2020 Ben Lewis.
# Licensed under the MIT license.

project('gd32vf103_sdk', 'c',
  version : '0.1',
  default_options : ['warning_level=3',
		     'default_library=static',
 		     'prefix=/opt/riscv'])

firmware_standard_path = 'Firmware' / 'GD32VF103_standard_peripheral'
fw_std_src = firmware_standard_path / 'Source'
fw_std_inc = firmware_standard_path / 'Include'
firmware_riscv_path = 'Firmware' / 'RISCV'
fw_riscv_drivers = firmware_riscv_path / 'drivers'
fw_riscv_stub = firmware_riscv_path / 'stubs'
firmware_src= [
  firmware_standard_path / 'system_gd32vf103.c',
  fw_std_src / 'gd32vf103_adc.c',
  fw_std_src / 'gd32vf103_dma.c',
  fw_std_src / 'gd32vf103_gpio.c',
  fw_std_src / 'gd32vf103_timer.c',
  fw_std_src / 'gd32vf103_bkp.c',
  fw_std_src / 'gd32vf103_eclic.c',
  fw_std_src / 'gd32vf103_i2c.c',
  fw_std_src / 'gd32vf103_usart.c',
  fw_std_src / 'gd32vf103_can.c',
  fw_std_src / 'gd32vf103_exmc.c',
  fw_std_src / 'gd32vf103_pmu.c',
  fw_std_src / 'gd32vf103_wwdgt.c',
  fw_std_src / 'gd32vf103_crc.c',
  fw_std_src / 'gd32vf103_exti.c',
  fw_std_src / 'gd32vf103_rcu.c',
  fw_std_src / 'gd32vf103_dac.c',
  fw_std_src / 'gd32vf103_fmc.c',
  fw_std_src / 'gd32vf103_rtc.c',
  fw_std_src / 'gd32vf103_dbg.c',
  fw_std_src / 'gd32vf103_fwdgt.c',
  fw_std_src / 'gd32vf103_spi.c',
  fw_riscv_drivers / 'n200_func.c',
  fw_riscv_stub / 'close.c',
  fw_riscv_stub / '_exit.c',
  fw_riscv_stub / 'fstat.c',
  fw_riscv_stub / 'isatty.c',
  fw_riscv_stub / 'lseek.c',
  fw_riscv_stub / 'read.c',
  fw_riscv_stub / 'sbrk.c',
  fw_riscv_stub / 'write.c',
  fw_riscv_stub / 'write_hex.c'
]

headers = [
  firmware_standard_path / 'gd32vf103.h',
  firmware_standard_path / 'system_gd32vf103.h',
  fw_std_inc / 'gd32vf103_adc.h',
  fw_std_inc / 'gd32vf103_bkp.h',
  fw_std_inc / 'gd32vf103_can.h',
  fw_std_inc / 'gd32vf103_crc.h',
  fw_std_inc / 'gd32vf103_dac.h',
  fw_std_inc / 'gd32vf103_dbg.h',
  fw_std_inc / 'gd32vf103_dma.h',
  fw_std_inc / 'gd32vf103_eclic.h',
  fw_std_inc / 'gd32vf103_exmc.h',
  fw_std_inc / 'gd32vf103_exti.h',
  fw_std_inc / 'gd32vf103_fmc.h',
  fw_std_inc / 'gd32vf103_fwdgt.h',
  fw_std_inc / 'gd32vf103_gpio.h',
  fw_std_inc / 'gd32vf103_i2c.h',
  fw_std_inc / 'gd32vf103_pmu.h',
  fw_std_inc / 'gd32vf103_rcu.h',
  fw_std_inc / 'gd32vf103_rtc.h',
  fw_std_inc / 'gd32vf103_spi.h',
  fw_std_inc / 'gd32vf103_timer.h',
  fw_std_inc / 'gd32vf103_usart.h',
  fw_std_inc / 'gd32vf103_wwdgt.h',
  fw_riscv_drivers / 'n200_eclic.h',
  fw_riscv_drivers / 'n200_func.h',
  fw_riscv_drivers / 'n200_timer.h',
  fw_riscv_drivers / 'riscv_bits.h',
  fw_riscv_drivers / 'riscv_const.h',
  fw_riscv_drivers / 'riscv_encoding.h',
  'Template' / 'gd32vf103_libopt.h'
]

incdir = include_directories(firmware_standard_path,
			     firmware_standard_path / 'Include',
			     fw_riscv_drivers,
			     fw_riscv_stub,
			     'Template')

cargs = ['-D HXTAL_VALUE=8000000',
	 '-march=rv32imac',
	 '-mabi=ilp32',
	]

sdk_lib = library('gd32vf103_sdk',
		  firmware_src,
		  c_args : cargs,
		  include_directories : incdir,
		  install: true
		 )

install_headers(headers, subdir: 'gd32vf103')

pkg = import('pkgconfig')
libs = [sdk_lib]
h = ['gd32vf103']
pkg.generate(libraries: libs,
	     subdirs: h,
	     version : '1.0',
	     name : 'libgd32vf103_sdk',
	     filebase: 'gd32vf103_sdk',
	     description: 'SDK library for the GigaDevices GD32VF103 MCU.')
		       
