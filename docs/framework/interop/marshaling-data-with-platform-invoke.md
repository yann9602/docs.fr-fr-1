---
title: "Marshaling de données à l’aide de l’appel de code managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71a4962029c0056287e97ea56dc02ae6cef8b603
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-platform-invoke"></a>Marshaling de données à l’aide de l’appel de code managé
Pour appeler des fonctions exportées depuis une bibliothèque non managée, une application .NET Framework a besoin d'un prototype de fonction dans du code managé qui représente la fonction non managée. Pour créer un prototype qui permette à un appel de code non managé de marshaler des données correctement, vous devez procédez comme suit :  
  
-   Appliquez l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> à la fonction ou à la méthode statique dans du code managé.  
  
-   Remplacez les types de données managés par des types de données non managés.  
  
 Vous pouvez utiliser la documentation fournie avec une fonction non managée pour construire un prototype managé équivalent en appliquant l'attribut et ses champs facultatifs, et en remplaçant les types de données managés par des types non managés. Pour obtenir des instructions sur l’application de **DllImportAttribute**, consultez [Consommation de fonctions DLL non managées](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Cette section fournit des exemples qui montrent comment créer des prototypes de fonctions managés pour passer des arguments et recevoir des valeurs de retour des fonctions exportées par des bibliothèques non managées. Les exemples montrent également quand utiliser l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> et la classe <xref:System.Runtime.InteropServices.Marshal> pour marshaler explicitement des données.  
  
## <a name="platform-invoke-data-types"></a>Types de données d'appel de code non managé  
 Le tableau suivant répertorie les types de données utilisés dans les fonctions de l'API Win32 (répertoriées dans Wtypes.h) et dans les fonctions de style C. De nombreuses bibliothèques non managées contiennent des fonctions qui passent ces types de données comme des paramètres et des valeurs de retour. La troisième colonne contient le type valeur ou la classe .NET Framework intégrés correspondants que vous utilisez dans le code managé. Dans certains cas, vous pouvez remplacer un type de la même taille par le type répertorié dans le tableau.  
  
|Type non managé dans Wtypes.h|Type de langage C non managé|Nom de classe managée|Description|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**HANDLE**|**void\***|<xref:System.IntPtr?displayProperty=nameWithType>|32 bits sur les systèmes d'exploitation Windows 32 bits, 64 bits sur les systèmes d'exploitation Windows 64 bits.|  
|**BYTE**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 bits|  
|**SHORT**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bits|  
|**WORD**|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|16 bits|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 bits|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32 bits|  
|**LONG**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32 bits|  
|**BOOL**|**long**|<xref:System.Byte>|32 bits|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bits|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bits|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|Décorer avec ANSI.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Décorer avec Unicode.|  
|**LPSTR**|**char\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Décorer avec ANSI.|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Décorer avec ANSI.|  
|**LPWSTR**|**wchar_t\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Décorer avec Unicode.|  
|**LPCWSTR**|**Const wchar_t\***|<xref:System.String?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Décorer avec Unicode.|  
|**FLOAT**|**Float**|<xref:System.Single?displayProperty=nameWithType>|32 bits|  
|**DOUBLE**|**Double**|<xref:System.Double?displayProperty=nameWithType>|64 bits|  
  
 Pour les types correspondants dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# et C++, consultez [Introduction à la bibliothèque de classes .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 Le code suivant définit les fonctions de bibliothèque fournies par Pinvoke.dll. De nombreux exemples décrits dans cette section appellent cette bibliothèque.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
