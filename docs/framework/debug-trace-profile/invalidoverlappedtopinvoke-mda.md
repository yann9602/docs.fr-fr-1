---
title: "invalidOverlappedToPinvoke MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "overlapped pointers"
  - "managed debugging assistants (MDAs), overlapped pointers"
  - "invalid overlapped pointer to platform invoke"
  - "InvalidOverlappedToPinvoke MDA"
  - "MDAs (managed debugging assistants), overlapped pointers"
  - "pointers, overlapped"
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# invalidOverlappedToPinvoke MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `invalidOverlappedToPinvoke` est activé lorsqu'un pointeur superposé qui n'a pas été créé sur le tas du garbage collection est passé à des fonctions Win32 spécifiques.  
  
> [!NOTE]
>  Par défaut, ce MDA est activé uniquement si l'appel de code non managé est défini dans votre code et que le débogueur signale l'état JustMyCode de chaque méthode.  Un débogueur qui ne comprend pas JustMyCode \(tel que MDbg.exe sans extension\) n'activera pas ce MDA.  Ce MDA peut être activé pour ces débogueurs en utilisant un fichier de configuration et en définissant explicitement `justMyCode="false"` dans le fichier de configuration .mda `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`\).  
  
## Symptômes  
 Incidents ou altérations de tas inexplicables.  
  
## Cause  
 Un pointeur superposé, qui n'a pas été créé sur le tas du garbage collection, est passé à des fonctions spécifiques du système d'exploitation.  
  
 Le tableau suivant répertorie les fonctions dont cet Assistant Débogage managé assure le suivi.  
  
|Module|Fonction|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|kernel32.dll|`ReadFile`|  
|kernel32.dll|`ReadFileEx`|  
|kernel32.dll|`WriteFile`|  
|kernel32.dll|`WriteFileEx`|  
|kernel32.dll|`ReadDirectoryChangesW`|  
|kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2\_32.dll|`WSASend`|  
|WS2\_32.dll|`WSASendTo`|  
|WS2\_32.dll|`WSARecv`|  
|WS2\_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Le risque d'altération de tas est élevé pour cette condition car le <xref:System.AppDomain> effectuant l'appel peut être déchargé.  En cas de déchargement de <xref:System.AppDomain>, soit le code d'application libérera de la mémoire pour le pointeur superposé, donnant lieu à une altération du tas GC au terme de l'opération, soit le code provoquera une fuite de mémoire, entraînant des problèmes ultérieurs.  
  
## Résolution  
 Utilisez un objet <xref:System.Threading.Overlapped>, appelant la méthode <xref:System.Threading.Overlapped.Pack%2A> pour obtenir une structure <xref:System.Threading.NativeOverlapped> qui peut être passée à la fonction.  Si le <xref:System.AppDomain> est déchargé, le CLR \(Common Language Runtime\) attend la fin de l'opération asynchrone avant de libérer le pointeur.  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## Sortie  
 Le message suivant constitue un exemple de sortie de cet Assistant Débogage managé.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'.  If the AppDomain is shut down, this can cause heap corruption when the async I/O completes.  The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack().  If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)