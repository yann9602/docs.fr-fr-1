---
title: "Marshaling a Delegate as a Callback Method | Microsoft Docs"
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
  - "data marshaling, Callback sample"
  - "marshaling, Callback sample"
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Marshaling a Delegate as a Callback Method
Cet exemple montre comment passer des délégués vers une fonction non managée qui attend des pointeurs fonction.  Un délégué est une classe qui peut contenir une référence à une méthode et qui équivaut à un pointeur fonction de type sécurisé.  
  
> [!NOTE]
>  Lorsque vous utilisez un délégué à l'intérieur d'un appel, le Common Language Runtime évite au délégué d'être récupéré par le garbage collector pendant la durée de cet appel.  Cependant, si la fonction non managée stocke le délégué pour utilisation après que l'appel soit terminé, vous devez manuellement empêcher le garbage collection jusqu'à ce que la fonction non managée en ait terminé avec le délégué.  Pour plus d'informations, consultez [HandleRef, exemple](http://msdn.microsoft.com/fr-fr/ab23b04e-1d53-4ec7-b27a-e892d9298959) et [GCHandle, exemple](http://msdn.microsoft.com/fr-fr/6acce798-0385-4ded-a790-77da842c113f).  
  
 L'exemple Callback utilise les fonctions non managées suivantes, illustrées avec leur déclaration de fonction d'origine :  
  
-   **TestCallBack** exportée à partir de PinvokeLib.dll.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** exportée à partir de PinvokeLib.dll.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/fr-fr/5d1438d7-9946-489d-8ede-6c694a08f614) est une bibliothèque non managée personnalisée qui contient une implémentation pour les fonctions précédemment répertoriées.  
  
 Dans cet exemple, la classe `LibWrap` contient des prototypes managés pour les méthodes `TestCallBack` et `TestCallBack2`.  Ces deux méthodes passent un délégué à une fonction de rappel sous la forme d'un paramètre.  La signature du délégué doit correspondre à la signature de la méthode qu'il référence.  Par exemple, les délégués `FPtr` et `FPtr2` ont des signatures qui sont identiques aux méthodes `DoSomething` et `DoSomething2`.  
  
## Déclaration de prototypes  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## Fonctions d'appel  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## Voir aussi  
 [Miscellaneous Marshaling Samples](http://msdn.microsoft.com/fr-fr/a915c948-54e9-4d0f-a525-95a77fd8ed70)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/fr-fr/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)