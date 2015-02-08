obj-$(CONFIG_MTK_PMIC)          += pmic_mt6323.o upmu_common.o

obj-$(CONFIG_MTK_SMART_BATTERY) += battery_meter_hal.o 

ifeq (true,$(strip $(TARGET_BUILD_MMITEST)))
    EXTRA_CFLAGS += -DBATT_ID_CHECK_SUPPORT=0 -DBATT_TEMP_FOR_MINI=1
else
    EXTRA_CFLAGS += -DBATT_ID_CHECK_SUPPORT=1 -DBATT_TEMP_FOR_MINI=0
endif

ifeq ($(MTK_BQ24196_SUPPORT),yes) 
    obj-$(CONFIG_MTK_SMART_BATTERY) += mt_battery_bq24196.o mt6320_fuel_gauge_bq24196.o bq24196.o
    ifeq ($(MTK_BQ27541_SUPPORT),yes)
      obj-$(CONFIG_MTK_SMART_BATTERY) += bq27541.o
    endif
else
  ifeq ($(MTK_NCP1851_SUPPORT),yes) 
    obj-$(CONFIG_MTK_SMART_BATTERY) += mt_battery_ncp1851.o mt6320_fuel_gauge_ncp1851.o ncp1851.o
  else
      ifeq ($(MTK_FAN5405_SUPPORT),yes)
           obj-$(CONFIG_MTK_SMART_BATTERY) += fan5405.o charging_hw_fan5405.o
      else
	   obj-$(CONFIG_MTK_SMART_BATTERY) += charging_hw_pmic.o 
      endif
  endif
endif
