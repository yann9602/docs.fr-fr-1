---
title: "Guide pratique pour utiliser les fonctionnalités de la documentation XML (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f4e74e2da4a5f8ba0a9964a5eff4f2a492b8981f
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Guide pratique pour utiliser les fonctionnalités de la documentation XML (Guide de programmation C#)
L’exemple suivant montre un type qui a été documenté.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **// Ce fichier .xml a été généré avec l’exemple de code précédent.**  
**\<?xml version="1.0"?>**  
**\<doc>**  
 **\<assembly>**  
 **\<name>xmlsample\</name>**  
 **\</assembly>**  
 **\<members>**  
 **\<member name="T:SomeClass">**  
 **\<summary>**  
 **Insérer ici les informations récapitulatives relatives à la classe.\</summary>**  
 **\<remarks>**  
 **Des commentaires plus longs peuvent être associés à un type ou à un membre**   
 **grâce à la balise remarks\</remarks>**  
 **\</member>**  
 **\<member name="F:SomeClass.m_Name">**  
 **\<summary>**  
 **Stocke la propriété name\</summary>**  
 **\</member>**  
 **\<member name="M:SomeClass.#ctor">**  
 **\<summary>Le constructeur de classe.\</summary>**   
 **\</member>**  
 **\<member name="M:SomeClass.SomeMethod(System.String)">**  
 **\<summary>**  
 **Description de la méthode SomeMethod.\</summary>**  
 **\<param name="s"> Insérer ici la description du paramètre s.\</param>**  
 **\<seealso cref="T:System.String">**  
 **Vous pouvez utiliser l’attribut cref sur n’importe quelle balise pour référencer un type ou un membre**   
 **et le compilateur vérifiera que cette référence existe. \</seealso>**  
 **\</member>**  
 **\<member name="M:SomeClass.SomeOtherMethod">**  
 **\<summary>**  
 **Autre méthode quelconque. \</summary>**  
 **\<returns>**  
 **Les résultats retournés sont décrits grâce à la balise returns.\</returns>**  
 **\<seealso cref="M:SomeClass.SomeMethod(System.String)">**  
 **Remarquez l’utilisation de l’attribut cref pour référencer une méthode spécifique \</seealso>**  
 **\</member>**  
 **\<member name="M:SomeClass.Main(System.String[])">**  
 **\<summary>**  
 **Point d’entrée de l’application.**  
 **\</summary>**  
 **\<param name="args"> Liste d’arguments de la ligne de commande\</param>**  
 **\</member>**  
 **\<member name="P:SomeClass.Name">**  
 **\<summary>**  
 **Propriété Name \</summary>**  
 **\<value>**  
 **Une balise value sert à décrire la valeur de la propriété\</value>**  
 **\</member>**  
 **\</members>**  
**\</doc>**   
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler l’exemple, tapez ce qui suit sur la ligne de commande :  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Cela créera le fichier XML XMLsample.xml, que vous pouvez afficher dans votre navigateur ou à l’aide de la commande TYPE.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le début de la documentation XML est symbolisé par trois barres obliques (///). Lorsque vous créez un projet, les Assistants insèrent quelques lignes de début (///) pour vous. Le traitement de ces commentaires présente certaines restrictions :  
  
-   La documentation doit être dans un format XML correct. Si le XML n’est pas correct, un avertissement est généré. En outre, un commentaire indiquant qu’une erreur s’est produite est ajouté au fichier de documentation.  
  
-   Les développeurs sont libres de créer leur propre jeu de balises. Il existe un jeu de balises recommandé (voir la section « Informations supplémentaires »). Certaines des balises recommandées ont des significations spéciales :  
  
    -   La balise \<param> est utilisée pour décrire les paramètres. Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. Si ce n’est pas le cas, le compilateur émet un avertissement.  
  
    -   L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code. Le compilateur vérifie l’existence de cet élément de code. Si ce n’est pas le cas, le compilateur émet un avertissement. Le compilateur respecte toutes les instructions `using` lorsqu’il recherche un type décrit dans l’attribut `cref`.  
  
    -   La balise \<summary> est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou un membre.  
  
        > [!NOTE]
        >  Le fichier XML ne fournit pas des informations complètes sur le type et les membres (par exemple, il ne contient pas d’informations sur le type). Pour obtenir des informations complètes sur un type ou sur un membre, le fichier de documentation doit être utilisé avec la réflexion sur le type ou sur le membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [/doc (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Commentaires sur la documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
