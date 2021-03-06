INCLUDE_DIRECTORIES( ${CMAKE_SOURCE_DIR}/src )
INCLUDE_DIRECTORIES( ${CMAKE_SOURCE_DIR}/src/EnergyPlus )

set( test_src
  AdvancedAFN.unit.cc
  AirflowNetworkSolver.unit.cc
  DataPlant.unit.cc
  DataZoneEquipment.unit.cc
  DXCoils.unit.cc
  EvaporativeCoolers.unit.cc
  ExteriorEnergyUse.unit.cc
  FluidCoolers.unit.cc
  GroundHeatExchangers.unit.cc
  HeatBalanceManager.unit.cc
  Humidifiers.unit.cc
  HVACStandaloneERV.unit.cc
  ManageElectricPower.unit.cc
  MixedAir.unit.cc
  PurchasedAirManager.unit.cc
  OutputProcessor.unit.cc
  OutputReportTabular.unit.cc
  ReportSizingManager.unit.cc
  SizingManager.unit.cc
  SolarShading.unit.cc
  SortAndStringUtilities.unit.cc
  SQLite.unit.cc
  Vectors.unit.cc
  Vector.unit.cc
  WaterThermalTanks.unit.cc
  main.cc
)
set( test_dependencies
  energyplusapi
 )

if(CMAKE_HOST_UNIX)
  if(NOT APPLE)
    list(APPEND test_dependencies dl )
  endif()
endif()

# Executable name will be EnergyPlus_tests
# Execute energyplus_tests --help for options using gtest runner
# Execute energyplus_tests with no arguments to run all tests
CREATE_TEST_TARGETS( energyplus "${test_src}" "${test_dependencies}" )
