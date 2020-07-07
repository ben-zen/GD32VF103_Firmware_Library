# Copyright 2020 Ben Lewis.
# Licensed under the MIT license.

project('gd32vf103_sdk', 'c',
  version : '0.1',
  default_options : ['warning_level=3', 'default_library=static'])

firmware_standard_path = 'Firmware' / 'GD32VF103_standard_peripheral'
fw_std_src = firmware_standard_path / 'Source'
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

incdir = include_directories(firmware_standard_path, firmware_standard_path / 'Include', fw_riscv_drivers, fw_riscv_stub, 'Template')

cargs = ['-D HXTAL_VALUE=8000000',]

library('gd32vf103_sdk', firmware_src,
	c_args : cargs,
	include_directories : incdir)
