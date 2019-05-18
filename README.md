# SCT test results

May 18th, 2019

The UEFI SCT test implementation has seperate routines for testing if parameters
are correctly checked (conformance tests) and if a function does it jobs
(function tests).

* FAIL signifies that at least one failure was reported. It does not imply that
  the function is not working at all.
* N/A signifies that no test for this category is available.

## Boot services

| Service                             | Conformance | Function   |
| ----------------------------------- | ----------- | ---------- |
|                                     |             |            |
| **Event, Timer, and Task Priority Services**                   |
| CreateEvent                         | PASS        | FAIL       |
| CreateEventEx                       | PASS        | FAIL       |
| CloseEvent                          | N/A         | PASS       |
| SignalEvent                         | N/A         | PASS       |
| WaitForEvent                        | PASS        | PASS       |
| CheckEvent                          | PASS        | PASS       |
| SetTimer                            | PASS        | FAIL       |
| RaiseTPL                            | N/A         | PASS       |
| Restore TPL                         | N/A         | PASS       |
|                                     |             |            |
| **Memory Allocation Services**                                 |
| AllocatePages                       | PASS        | PASS       |
| FreePages                           | PASS        | PASS       |
| GetMemoryMap                        | PASS        | PASS       |
| AllocatePool                        | PASS        | PASS       |
| FreePool                            | PASS        | PASS       |
|                                     |             |            |
| **Protocol Handler Services**                                  |
| InstallProtocolInterface            | PASS        | PASS       |
| UninstallProtocolInterface          | PASS        | FAIL       |
| ReinstallProtocolInterface          | PASS        | FAIL       |
| RegisterProtocolNotify              | PASS        | PASS       |
| LocateHandle                        | PASS        | FAIL       |
| HandleProtocol                      | PASS        | PASS       |
| LocateDevicePath                    | PASS        | FAIL       |
| OpenProtocol                        | PASS        | CRASH      |
| CloseProtocol                       | PASS        | PASS       |
| OpenProtocolInformation             | PASS        | FAIL       |
| ConnectController                   | PASS        | FAIL       |
| DisconnectController                | PASS        | FAIL       |
| ProtocolsPerHandle                  | PASS        | PASS       |
| LocateHandleBuffer                  | PASS        | FAIL       |
| LocateProtocol                      | PASS        | FAIL       |
| InstallMultipleProtocolInterfaces   | PASS        | PASS       |
| UninstallMultipleProtocolInterfaces | PASS        | FAIL       |
|                                     |             |            |
| **Images Services**                                            |
| LoadImage                           | FAIL        | FAIL       |
| StartImage                          | PASS        | FAIL       |
| UnloadImage                         | PASS        | FAIL       |
| Exit                                | PASS        | FAIL       |
| ExitBootServices                    | N/A         | FAIL       |
|                                     |             |            |
| **Miscellaneous Boot Services**                                |
| SetWatchDogTimer                    | N/A         | FAIL       |
| Stall                               | N/A         | PASS       |
| CopyMem                             | N/A         | PASS       |
| SetMem                              | N/A         | PASS       |
| GetNextMonotonicCount               | PASS        | FAIL       |
| InstallConfigurationTable           | PASS        | PASS       |
| CalculateCrc32                      | PASS        | PASS       |
|                                     |             |            |


## Protcols

| Protocol                            | Conformance | Function   |
| ----------------------------------- | ----------- | ---------- |
|                                     |             |            |
| **LoadedImageProtocol**                           |            |
| Test 1                              | N/A         | PASS       |
| Teet 2                              | N/A         | PASS       |
|                                     |             |            |
| **UnicodeCollationProtocol**                                   |
| FatToStr                            | N/A         | PASS       |
| MetaiMatch                          | N/A         | FAIL       |
| StriColl                            | N/A         | PASS       |
| StrLwr                              | N/A         | PASS       |
| StrToFat                            | N/A         | FAIL       |
| StrUpr                              | N/A         | FAIL       |
|                                     |             |            |


## ConsoleSupportTest

| Test                                | Conformance | Function   |
| ----------------------------------- | ----------- | ---------- |
|                                     |             |            |
| SimpleTextInputExProtocolTest       | FAIL 1)     | N/A        |
| SimpleInputProtocolTest             | PASS        | N/A        |
| SimpleOutputProtocolTest            | N/A         | CRASH      |
|                                     |             |            |

1) SetToggleState returns EFI\_UNSUPPORTED. SCT expected
   EFI\_INVALID\_PARAMETER for invalid parameter. Testing a parameter
   for an unsupported function does not make much sense.

