---
title: "MsgBox Sample | Microsoft Docs"
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
  - "marshaling, MsgBox sample"
  - "data marshaling, MsgBox sample"
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# MsgBox Sample
Cet exemple montre comment passer des types chaîne par valeur comme paramètres en entrée et quand utiliser les champs <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> et <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.  
  
 L'exemple MsgBox utilise la fonction non managée suivante, illustrée avec sa déclaration de fonction d'origine :  
  
-   **MessageBox** exportée à partir de User32.dll.  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 Dans cet exemple, la classe `LibWrap` contient un prototype managé pour chaque fonction non managée appelée par la classe `MsgBoxSample`.  Les méthodes de prototype managé `MsgBox`, `MsgBox2`, et `MsgBox3` possèdent différentes déclarations pour la même fonction non managée.  
  
 La déclaration pour `MsgBox2` produit un résultat incorrect dans le message car le type caractère, spécifié comme étant ANSI, est incompatible avec le point d'entrée `MessageBoxW`, qui est le nom de la fonction Unicode.  La déclaration pour `MsgBox3` crée une incompatibilité entre les champs **EntryPoint**, **CharSet** et **ExactSpelling**.  Lorsqu'elle est appelée, `MsgBox3` lève une exception.  Pour plus d'informations sur l'affectation de noms de chaînes et le marshaling de nom, consultez [Spécification d'un jeu de caractères](../../../docs/framework/interop/specifying-a-character-set.md).  
  
## Déclaration de prototypes  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## Fonctions d'appel  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## Voir aussi  
 [Marshaling Strings](../../../docs/framework/interop/marshaling-strings.md)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/fr-fr/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [Default Marshaling for Strings](../../../docs/framework/interop/default-marshaling-for-strings.md)   
 [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [Spécification d'un jeu de caractères](../../../docs/framework/interop/specifying-a-character-set.md)