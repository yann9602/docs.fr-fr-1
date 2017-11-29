---
title: "Single, type de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c91dbdf73ed1e26393518001ec8651557e5b780f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="single-data-type-visual-basic"></a>Single, type de données (Visual Basic)
Contient des nombres à virgule flottante IEEE 32 bits (4 octets) simple précision compris entre - 3,4028235E + 38 signés et - 1, 401298E-45 pour les valeurs négatives et entre 1, 401298E-45 et 3,4028235E + 38 pour les valeurs positives. Nombres en simple précision stockent une approximation d’un nombre réel.  
  
## <a name="remarks"></a>Remarques  
 Utilisez le `Single` type de données pour contenir des valeurs à virgule flottante qui ne nécessitent pas la largeur totale des données de `Double`. Dans certains cas, le common language runtime peut être en mesure de compresser vos `Single` variables étroitement ensemble et d’enregistrer la consommation de mémoire.  
  
 La valeur par défaut de `Single` est 0.  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
-   **Précision.** Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours de représentation précise dans la mémoire. Cela peut entraîner des résultats inattendus à partir de certaines opérations, telles que la comparaison de valeurs et les `Mod` opérateur. Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Étendues.** Le `Single` type de données s’étend à `Double`. Cela signifie que vous pouvez convertir `Single` à `Double` sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.  
  
-   **Les zéros à droite.** Les types de données à virgule flottante n’ont pas d’aucune représentation interne du 0 de fin. Par exemple, ils n’effectuent pas distinction entre 4,2000 et 4.2. Par conséquent, les caractères 0 de fin n’apparaissent pas lorsque vous affichez ou imprimez les valeurs à virgule flottante.  
  
-   **Caractères de type.** L'ajout du caractère de type littéral `F` à un littéral force ce dernier en type de données `Single`. L'ajout du caractère de type identificateur `!` à un identificateur force ce dernier en type `Single`.  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Single?displayProperty=nameWithType>  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal (type de données)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double (type de données)](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
