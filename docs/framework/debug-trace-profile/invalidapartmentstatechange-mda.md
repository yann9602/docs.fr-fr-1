---
title: "invalidApartmentStateChange MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid apartment state"
  - "managed debugging assistants (MDAs), invalid apartment state"
  - "InvalidApartmentStateChange MDA"
  - "invalid apartment state changes"
  - "threading [.NET Framework], apartment states"
  - "apartment states"
  - "threading [.NET Framework], managed debugging assistants"
  - "COM apartment states"
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# invalidApartmentStateChange MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `invalidApartmentStateChange` est activé par l'un des deux problèmes suivants :  
  
-   Une tentative est effectuée pour modifier l'état de cloisonnement COM d'un thread qui a déjà été initialisé par COM à un état de cloisonnement différent.  
  
-   L'état de cloisonnement COM d'un thread change de manière inopinée.  
  
## Symptômes  
  
-   L'état de cloisonnement COM d'un thread ne correspond pas à ce qui a été demandé.  Cela peut entraîner l'utilisation de proxies pour des composants COM qui ont un modèle de thread différent du modèle courant.  Cela peut également provoquer la levée d'une <xref:System.InvalidCastException> lors de l'appel de l'objet COM via des interfaces qui ne sont pas définies pour le marshaling d'intercloisonnement.  
  
-   L'état de cloisonnement COM du thread est différent de celui qui est attendu.  Cela peut provoquer une <xref:System.Runtime.InteropServices.COMException> avec un HRESULT de RPC\_E\_WRONG\_THREAD ainsi qu'une <xref:System.InvalidCastException> lorsque des appels sont effectués sur un [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW\).  Cela peut également conduire plusieurs threads à accéder en même temps à certains composants COM STA \(Single\-Threaded Apartment\), ce qui risque d'entraîner l'altération ou la perte de données.  
  
## Cause  
  
-   Le thread a été précédemment initialisé à un état de cloisonnement COM différent.  Notez que l'état de cloisonnement d'un thread peut être défini explicitement ou implicitement.  Les opérations explicites incluent la propriété <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName> et les méthodes <xref:System.Threading.Thread.SetApartmentState%2A> et <xref:System.Threading.Thread.TrySetApartmentState%2A>.  <xref:System.Threading.ApartmentState> est implicitement affecté à un thread créé à l'aide de la méthode <xref:System.Threading.Thread.Start%2A>, à moins que <xref:System.Threading.Thread.SetApartmentState%2A> soit appelé avant le démarrage du thread.  De même, la valeur <xref:System.Threading.ApartmentState> est implicitement affectée au thread principal de l'application, à moins que l'attribut <xref:System.STAThreadAttribute> soit spécifié sur la méthode principale.  
  
-   La méthode `CoUninitialize` \(ou la méthode `CoInitializeEx`\) avec un modèle d'accès concurrentiel différent est appelée sur le thread.  
  
## Résolution  
 Définissez l'état de cloisonnement du thread avant que son exécution commence ou appliquez l'attribut <xref:System.STAThreadAttribute> ou l'attribut <xref:System.MTAThreadAttribute> à la méthode principale de l'application.  
  
 Dans l'idéal, pour la deuxième cause, le code qui appelle la méthode `CoUninitialize` doit être modifié pour différer l'appel jusqu'à ce que le thread soit sur le point de s'arrêter et qu'aucun des RCW ou leurs composants COM sous\-jacents ne soient encore utilisés par le thread.  Toutefois, s'il est impossible de modifier le code qui appelle la méthode `CoUninitialize`, aucun RCW ne doit être utilisé par des threads non initialisés de cette façon.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  
  
## Sortie  
 L'état de cloisonnement COM du thread actuel et l'état que le code tentait d'appliquer.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant illustre une situation qui peut activer ce MDA.  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)