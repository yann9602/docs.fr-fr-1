---
title: "Valeurs numériques dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 087c1cc56abf2a00544e22023ce72fae670df369
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="numerics-in-the-net-framework"></a>Valeurs numériques dans le .NET Framework
Le .NET Framework prend en charge les primitives numériques standard pour les intégraux et les nombres à virgule flottante, ainsi que <xref:System.Numerics.BigInteger>, un type intégral sans limite théorique supérieure ou inférieure, <xref:System.Numerics.Complex>, un type qui représente des nombres complexes et un ensemble de types de vecteurs compatibles SIMD dans l’espace de noms <xref:System.Numerics>.  
  
 De plus, System.Numerics.Vectors, la bibliothèque de types de vecteurs compatibles SIMD a été publiée sous forme de package NuGet.  
  
## <a name="integral-types"></a>Types intégraux  
 Le .NET Framework prend en charge les entiers signés et non signés, d'une longueur de un à huit octets. Le tableau suivant répertorie les types intégraux et leur taille, indique s'ils sont signés ou non signés, et spécifie leur plage de valeurs. Tous les entiers sont des types valeur.  
  
|Type|Signé/Non signé|Taille (en octets)|Valeur minimale|Valeur maximale|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=fullName>|Non signé|1|0|255|  
|<xref:System.Int16?displayProperty=fullName>|Signé|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=fullName>|Signé|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=fullName>|Signé|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=fullName>|Signé|1|-128|127|  
|<xref:System.UInt16?displayProperty=fullName>|Non signé|2|0|65,535|  
|<xref:System.UInt32?displayProperty=fullName>|Non signé|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=fullName>|Non signé|8|0|18 446 744 073 709 551 615|  
  
 Chaque type intégral prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et de conversion implicite. Chaque entier comprend également des méthodes pour effectuer des comparaisons d'égalité et des comparaisons relatives, pour convertir la représentation sous forme de chaîne d'un nombre en cet entier et pour convertir un entier en sa représentation sous forme de chaîne. Certaines autres opérations mathématiques en dehors de celles qui sont gérées par les opérateurs standard, comme l'arrondi et l'identification de la valeur plus grande ou plus petite de deux entiers, sont disponibles à partir de la classe <xref:System.Math>. Vous pouvez également travailler avec les bits individuels d'une valeur d'entier en utilisant la classe <xref:System.BitConverter>.  
  
 Notez que les types intégraux non signés ne sont pas conformes à CLS. Pour plus d’informations, consultez [Indépendance du langage et composants indépendants du langage](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Types virgule flottante  
 Le .NET Framework comprend trois types à virgule flottante primitifs, qui sont répertoriés dans le tableau suivant.  
  
|Type|Taille (en octets)|Minimum|Maximum|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=fullName>|8|-1,79769313486232e308|1,79769313486232e308|  
|<xref:System.Single?displayProperty=fullName>|4|-3,402823e38|3,402823e38|  
|<xref:System.Decimal?displayProperty=fullName>|16|-79 228 162 514 264 337 593 543 950 335|79 228 162 514 264 337 593 543 950 335|  
  
 Chaque type virgule flottante prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et de conversion implicite. Chacun comprend également des méthodes pour effectuer des comparaisons d'égalité et des comparaisons relatives, pour convertir la représentation sous forme de chaîne d'un nombre en virgule flottante et pour convertir un en nombre en virgule flottante en sa représentation sous forme de chaîne. Certaines autres opérations mathématiques, algébriques et trigonométriques sont disponibles à partir de la classe <xref:System.Math>. Vous pouvez également travailler avec les bits individuels de valeurs <xref:System.Double> et <xref:System.Single> en utilisant la classe <xref:System.BitConverter>. La structure <xref:System.Decimal?displayProperty=fullName> a ses propres méthodes, <xref:System.Decimal.GetBits%2A?displayProperty=fullName> et <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=fullName> pour travailler avec les bits individuel d'une valeur décimale, ainsi que son propre ensemble de méthodes pour effectuer d'autres opérations mathématiques.  
  
 Les types <xref:System.Double> et <xref:System.Single> sont destinés à être utilisé pour des valeurs par nature imprécises (par exemple la distance entre deux étoiles dans le système solaire) et les applications dans lesquelles un haut degré de précision et une erreur d'arrondi réduite ne sont pas des impératifs. Vous devez utiliser le type <xref:System.Decimal?displayProperty=fullName> pour les cas dans lesquels une plus grande précision est requise et où les erreurs d'arrondi ne sont pas souhaitables.  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=fullName> est un type immuable qui représente un entier arbitrairement grand dont la valeur en théorie n'a pas de limite supérieure ou inférieure. Les méthodes du type <xref:System.Numerics.BigInteger> sont très proches de celles des autres types intégraux.  
  
## <a name="complex"></a>Complex  
 Le type <xref:System.Numerics.Complex> représente un nombre complexe, c'est-à-dire un nombre avec une partie réelle et une partie imaginaire. Il prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et de conversion implicite, ainsi que des méthodes mathématiques, algébriques et trigonométriques.  
  
## <a name="simd-enabled-vector-types"></a>Types de vecteurs compatibles SIMD  
 L’espace de noms <xref:System.Numerics> comprend un ensemble de types de vecteurs compatibles SIMD pour le .NET Framework. SIMD (opérations Single Instruction Multiple Data) permet à certaines opérations d’être parallélisées au niveau du matériel, ce qui se traduit par une nette amélioration des performances des applications mathématiques, scientifiques et graphiques qui effectuent des calculs sur les vecteurs.  
  
 Les types de vecteurs compatibles SIMD rencontrés dans le .NET Framework sont les suivants :  De plus, System.Numerics.Vectors inclut un type Plane et un type Quaternion.  
  
-   Les types <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> et <xref:System.Numerics.Vector4>, qui correspondent à des vecteurs à 2, 3 et 4 dimensions de type <xref:System.Single>.  
  
-   Deux types de matrices, <xref:System.Numerics.Matrix3x2>, qui représente une matrice 3 x 2, et <xref:System.Numerics.Matrix4x4>, qui représente une matrice 4 x 4.  
  
-   Les types <xref:System.Numerics.Plane> et <xref:System.Numerics.Quaternion>.  
  
 Les types de vecteurs compatibles SIMD sont implémentés en langage intermédiaire, ce qui permet de les utiliser sur un matériel non compatible SIMD et sur les compilateurs JIT. Pour tirer parti des instructions SIMD, vos applications 64 bits doivent être compilées par le nouveau compilateur JIT 64 bits pour le code managé, qui est intégré au.NET Framework 4.6 ; il ajoute la prise en charge SIMD quand les processeurs x64 sont ciblés.  
  
 SIMD peut aussi être téléchargé sous forme de [NuGet package](http://www.nuget.org/packages/System.Numerics.Vectors).  Le package NuGet inclut aussi une structure <xref:System.Numerics.Vector%601> générique, qui permet de créer un vecteur de n’importe quel type numérique primitif. (Les types numériques primitifs incluent tous les types numériques de l'espace de noms <xref:System> à l'exception de <xref:System.Decimal>.) De plus, la structure <xref:System.Numerics.Vector%601> fournit une bibliothèque de méthodes pratiques que vous pouvez appeler quand vous utilisez des vecteurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Application Essentials](../../docs/standard/application-essentials.md)

