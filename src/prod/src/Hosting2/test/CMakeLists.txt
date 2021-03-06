include_directories("..")

add_compile_options(-rdynamic)

add_definitions(-DBOOST_TEST_ENABLED)
add_definitions(-DNO_INLINE_EVENTDESCCREATE)

add_executable(${exe_Hosting2Test}
  # boost.test main
  ../../../test/BoostUnitTest/btest.cpp

  # test code
  ../ProcessActivator.Linux.Test.cpp
  ../DummyStatelessServiceFactory.Test.cpp
  ../NonActivatedApplicationHost.Test.cpp
  ../CodePackageAcivationContext.Test.cpp
  ../DownloadManager.Test.cpp
  ../IPAddressProvider.Test.cpp
  ../ReservationManager.Test.cpp
  ../FlatIPConfiguration.Test.cpp
  ../IPAM.Test.cpp
  ../DownloadManagerFSSSetup.Test.cpp
  ../ServiceTypeStateManager.Test.cpp
  ../FabricNodeHost.Test.cpp
  ../FabricUpgrade.Test.cpp
  ../WorkingFolder.Test.cpp
  ../ApplicationUpgrade.Test.cpp
  ../LocalResourceManager.Test.cpp
  ../GuestServiceTypeHostManager.Test.cpp
  ../EnvironmentManager.Test.cpp
  )

add_precompiled_header(${exe_Hosting2Test} ../stdafx.h)

set_target_properties(${exe_Hosting2Test} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${TEST_OUTPUT_DIR}) 

target_link_libraries(${exe_Hosting2Test}
  ${lib_Hosting2}
  ${lib_FabricNode}
  ${lib_Testability}
  ${lib_Common}
  ${lib_ServiceModel}
  ${lib_Serialization}
  ${lib_ManagementSubsystem}
  ${lib_UpgradeOrchestrationService}
  ${lib_FaultAnalysisService}
  ${lib_BackupRestoreService}
  ${lib_ManagementCommon}
  ${lib_ImageStore}
  ${lib_ClusterManager}
  ${lib_Store}
  ${lib_TestHooks}
  ${lib_TStore}
  ${lib_Communication}
  ${lib_KtlLogger}
  ${lib_Client}
  ${lib_EntreeService}
  ${lib_StoreService}
  ${lib_EntreeService}
  ${lib_StoreService}
  ${lib_SystemServices}
  ${lib_Federation}
  ${lib_Hosting2}
  ${lib_Query}
  ${lib_ApiWrappers}
  ${lib_ClientServerTransport}
  ${lib_Transport}
  ${lib_Failover}
  ${lib_LoadBalancing}
  ${lib_FailoverCommon}
  ${lib_Replication}
  ${lib_HealthManager}
  ${lib_ImageStore}
  ${lib_FileStoreService}
  ${lib_UpgradeService}
  ${lib_ServiceModel}
  ${lib_ImageModel}
  ${lib_SystemServices}
  ${lib_StoreRepairPolicy}
  ${lib_FabricGateway}
  ${lib_httpgateway}
  ${lib_httptransport}
  ${lib_ManagementRepairManager}
  ${Casablanca_LIBRARIES}
  ${lib_EntreeService}
  ${lib_LeaseAgent}
  ${lib_Lease}
  ${lib_Replication}
  ${lib_Common}
  ${lib_TransactionalReplicator}
  ${lib_ServiceGroup}
  ${lib_ApiWrappers}
  ${lib_AadWrapperServer}
  ${lib_FabricUUID}
  ${lib_InternalFabricUUID}
  ${lib_DnsServiceConfig}
  ${KtlUser}
  ${KtlLoggerUser}
  ${lib_KtlLoggerShimUPassthrough}
  ${KtlLoggerUser}
  ${Ktlfull}
  ${BoostTest2}
  ${Cxx}
  ${CxxABI}
  ${lib_FabricCommon}
  ${lib_FabricResources}
  ssh2
  snappy
  lz4
  minizip
  z
  bz2
  m
  rt
  jemalloc
  pthread
  dl
  xml2
  uuid
  unwind
  unwind-x86_64
)

install(
    FILES ./Hosting2.Test.exe.cfg
    DESTINATION ${TEST_OUTPUT_DIR}
)

install(
    FILES ./RunHosting2Tests.sh
    PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ
    DESTINATION ${TEST_OUTPUT_DIR}
)

# Following are copying data from source directory
install(
    DIRECTORY 
    DESTINATION ${TEST_OUTPUT_DIR}/Hosting.Test.Data 
)

install(
    DIRECTORY ./Data/ActivationContextTest ./Data/ChangeNotificationData
    DESTINATION ${TEST_OUTPUT_DIR}/Hosting.Test.Data
)

install(
    DIRECTORY 
    DESTINATION ${TEST_OUTPUT_DIR}/Hosting.Test.Data/ImageStoreRoot
)

install(
    DIRECTORY ./Data/WindowsFabricStore
    DESTINATION ${TEST_OUTPUT_DIR}/Hosting.Test.Data/ImageStoreRoot
)

install(
    DIRECTORY 
    DESTINATION ${TEST_OUTPUT_DIR}/Hosting.Test.Data/ImageStoreRoot/Store
)

install(
    DIRECTORY ./Data/CalculatorApp ./Data/SandboxPersistentQueueApp ./Data/WorkingFolderTestApp ./Data/AppUpgradeApp
    DESTINATION ${TEST_OUTPUT_DIR}/Hosting.Test.Data/ImageStoreRoot/Store
)

