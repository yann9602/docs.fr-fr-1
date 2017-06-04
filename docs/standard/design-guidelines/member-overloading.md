---
title: "Surcharge de membre | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "arguments par défaut"
  - "membres (.NET Framework), surchargées"
  - "règles de conception de membres (.NET Framework), la surcharge"
  - "membres surchargés"
  - "signatures de membres"
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Surcharge de membre
Surcharge de membre revient à créer deux membres ou plus sur le même type que le même nom mais diffèrent uniquement dans le nombre ou le type des paramètres. Par exemple, dans ce qui suit, la `WriteLine` méthode est surchargée :  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
  
```  
  
 Étant donné que seuls les constructeurs, les méthodes et propriétés indexées peuvent avoir des paramètres, seuls les membres peuvent être surchargés.  
  
 La surcharge est une des techniques plus importants pour améliorer la facilité d’utilisation, la productivité et la lisibilité des bibliothèques réutilisables. La surcharge sur le nombre de paramètres rend possible fournir des versions plus simples des constructeurs et méthodes. La surcharge sur le type de paramètre permet d’utiliser le même nom de membre pour effectuer des opérations identiques sur un ensemble sélectionné de différents types de membres.  
  
 **✓ faire** essaie d’utiliser des noms de paramètres descriptifs pour indiquer la valeur par défaut utilisée par les surcharges plus courtes.  
  
 **X éviter** Variant de façon arbitraire les noms de paramètres dans les surcharges. Si un paramètre d’une surcharge représente la même entrée en tant que paramètre dans une autre surcharge, les paramètres doivent avoir le même nom.  
  
 **X éviter** incohérentes dans l’ordre des paramètres de surcharge membres. Paramètres portant le même nom doivent apparaître dans la même position dans toutes les surcharges.  
  
 **✓ faire** rendez uniquement la surcharge la plus longue virtuelle \(si l’extensibilité est requise\). Les surcharges plus courtes doivent appeler simplement une surcharge plus longue.  
  
 **X ne pas** utiliser `ref` ou `out` modificateurs pour surcharger des membres.  
  
 Certaines langues ne peut pas résoudre les appels aux surcharges comme suit. En outre, ces surcharges ont généralement une sémantique complètement différente et ne doivent pas être surcharges mais deux méthodes distinctes à la place.  
  
 **X ne pas** ont des surcharges avec des paramètres à la même position et les types similaires, mais avec une sémantique différente.  
  
 **✓ faire**  autoriser `null` à passer les arguments facultatifs.  
  
 **✓ faire** utiliser membre surcharge plutôt que de définir les membres avec des arguments par défaut.  
  
 Arguments par défaut ne sont pas conformes CLS.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)