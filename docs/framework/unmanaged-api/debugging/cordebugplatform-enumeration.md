---
title: CorDebugPlatform-Enumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugPlatformEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugPlatformEnum
helpviewer_keywords: CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52842d40895a658ec9dbb1263f18c48ec999a0ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform-Enumeration
Stellt Zielplattformwerte, mit denen, die [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|Die Zielplattform ist Windows auf Intel-x86-Hardware.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Die Zielplattform ist 64-Bit-Windows auf AMD64-Hardware oder Intel EM64T-Hardware.|  
|CORDB_PLATFORM_WINDOWS_IA64|Die Zielplattform ist 32-Bit-Windows auf Intel IA-64-Hardware.|  
|CORDB_PLATFORM_MAC_PPC|Die Zielplattform ist Macintosh-Betriebssystem auf PowerPC-Hardware ausgeführt wird.|  
|CORDB_PLATFORM_MAC_X86|Die Zielplattform ist Macintosh-Betriebssystem auf Intel X86 Hardware ausgeführt wird.|  
|CORDB_PLATFORM_WINDOWS_ARM|Die Zielplattform ist Macintosh-Betriebssystem auf Windows-ARM-Hardware ausgeführt wird.|  
|CORDB_PLATFORM_MAC_AMD64|Die Zielplattform ist Macintosh-Betriebssystem auf AMD64-Hardware ausgeführt wird.|  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 Die `CORDB_PLATFORM_WINDOWS_ARM`- und `CORDB_PLATFORM_MAC_AMD64`-Member sind in .NET Framework 4.5.2 und höheren Versionen verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Enumerationen](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)