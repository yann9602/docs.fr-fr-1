---
title: "Comment&#160;: utiliser les fonctionnalit&#233;s de la documentation XML (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "documentation XML (C#)"
  - "Langage c#, les fonctionnalités de documentation XML"
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# Comment&#160;: utiliser les fonctionnalit&#233;s de la documentation XML (Guide de programmation C#)
L’exemple suivant fournit une vue d’ensemble d’un type qui a été documenté.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **Ce fichier .xml a été généré avec l’exemple de code précédent.**  
**\< ? xml version = « 1.0 » ?>**  
**\< doc>**  
 **\< assembly>**  
 **\< nom>xmlsample \< /name>**  
 **\< / assembly>**  
 **\< membres>**  
 **\< nom de membre = « T:SomeClass »>**  
 **\< résumé>**  
 **Documentation de résumé de niveau classe passe ici. \< / récapitulatif>**  
 **\< notes>**  
 **Un commentaire plus long peut être associé à un type ou membre**   
 **Grâce à la balise de notes \< / Remarques>**  
 **\< / membre>**  
 **\< membre name="F:SomeClass.m_Name »>**  
 **\< résumé>**  
 **Magasin pour la propriété nom \< / récapitulatif>**  
 **\< / membre>**  
 **\< nom de membre = « M:SomeClass. #ctor »>**  
 **\< Résumé>le constructeur de classe. \< / récapitulatif>**   
 **\< / membre>**  
 **\< membre name="M:SomeClass.SomeMethod(System.String) »>**  
 **\< résumé>**  
 **Description de SomeMethod. \< / récapitulatif>**  
 **\< param nom = « s »> description du paramètre de s ici \< / param>**  
 **\< seealso cref="T:System.String »>**  
 **Vous pouvez utiliser l’attribut cref sur n’importe quelle balise pour faire référence à un type ou membre**   
 **et le compilateur vérifiera que cette référence existe. \< / seealso>**  
 **\< / membre>**  
 **\< membre name="M:SomeClass.SomeOtherMethod »>**  
 **\< résumé>**  
 **Une autre méthode. \< / récapitulatif>**  
 **\< retourne>**  
 **Retourner les résultats sont décrits via la balise retourne. \< / renvoie>**  
 **\< seealso cref="M:SomeClass.SomeMethod(System.String) »>**  
 **Notez l’utilisation de l’attribut cref pour faire référence à une méthode spécifique à \< / seealso>**  
 **\< / membre>**  
 **\< membre name="M:SomeClass.Main(System.String[]) »>**  
 **\< résumé>**  
 **Le point d’entrée pour l’application.**  
 **\< / récapitulatif>**  
 **\< param nom = « arguments »> une liste d’arguments de ligne de commande \< / param>**  
 **\< / membre>**  
 **\< membre name="P:SomeClass.Name »>**  
 **\< résumé>**  
 **La propriété du nom \< / récapitulatif>**  
 **\< valeur>**  
 **Une balise value sert à décrire la valeur de propriété \< / valeur>**  
 **\< / membre>**  
 **\< / membres>**  
**\< / doc>**   
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler l’exemple, tapez la ligne de commande suivante :  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Cela créera le fichier XML XMLsample.xml, que vous pouvez afficher dans votre navigateur ou à l’aide de la commande TYPE.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Documentation XML commence par / / /. Lorsque vous créez un nouveau projet, les Assistants insèrent quelques lignes / / / starter dans pour vous. Le traitement de ces commentaires présente certaines restrictions :  
  
-   La documentation doit être correcte XML. Si le XML n’est pas correct, un avertissement est généré et le fichier de documentation contiendra un commentaire indiquant qu’une erreur s’est produite.  
  
-   Les développeurs sont libres de créer leur propre jeu de balises. Il existe un jeu de balises (voir la section informations supplémentaires) recommandé. Certaines des balises recommandées ont des significations spéciales :  
  
    -   Le \< param> balise est utilisée pour décrire les paramètres. Si utilisé, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. Si la vérification a échoué, le compilateur émet un avertissement.  
  
    -   Le `cref` attribut pouvant être joints à n’importe quelle balise pour fournir une référence à un élément de code. Le compilateur vérifie l’existence de cet élément de code. Si la vérification a échoué, le compilateur émet un avertissement. Le compilateur respecte les `using` lorsqu’il recherche un type décrit dans le `cref` attribut.  
  
    -   Le \< Résumé> balise est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou membre.  
  
        > [!NOTE]
        >  Le fichier XML ne fournit pas des informations complètes sur le type et les membres (par exemple, il ne contient aucune information de type). Pour obtenir des informations complètes sur un type ou un membre, vous devez utiliser le fichier de documentation avec la réflexion sur le type réel ou d’un membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation c#](../../../csharp/programming-guide/index.md)   
 [/doc (Options du compilateur c#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Commentaires de Documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)