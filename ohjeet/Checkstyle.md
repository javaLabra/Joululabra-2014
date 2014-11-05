# Checkstyle

Koodin testauksen lisäksi koodin luettavuuden ylläpitäminen on tärkeää, tässä hyvänä apuvälineenä on staattisen analyysin työkalu checkstyle ks. [http://checkstyle.sourceforge.net/](http://checkstyle.sourceforge.net/)

>Checkstyle is a development tool to help programmers write Java code that adheres to a coding standard. It automates the process of checking Java code to spare humans of this boring (but important) task. This makes it ideal for projects that want to enforce a coding standard.

### Checkstylen tuominen projektiin

Checkstyle on helppo tuoda Maven-projektiin, lisätään se vain **pom.xml** tiedostoon. Jotta Checkstyle raporteista pääsee helposti tarkastelemaan lähdekoodissa olevaa ongelma kohtaa on hyvä käyttää Checkstyleä yhdessä [jxr:n](http://maven.apache.org/plugins/maven-jxr-plugin/) kanssa. 

Lisää **pom.xml** tiedostoon
```
<reporting>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-checkstyle-plugin</artifactId>
      <version>2.13</version>
    </plugin>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-jxr-plugin</artifactId>
      <version>2.4</version>
    </plugin>
  </plugins>
</reporting>
```

Checkstylen tarkkailemien virheiden joukko on konfiguroitavissa erillisen konfiguraatiotiedoston avulla, luo nyt tätä varten projektiin uusi **XML**-tiedosto jolle voit antaa nimeksi esimerkiksi _checkstyle.xml_. 

Esimerkki konfiguraatiotiedostosta:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE module PUBLIC "-//Puppy Crawl//DTD Check Configuration 1.3//EN" "http://www.puppycrawl.com/dtds/configuration_1_3.dtd">
<module name="Checker">
    <module name="StrictDuplicateCode">
        <property name="min" value="10"/>
    </module>
    <module name="TreeWalker">
        <module name="RedundantImport"/>
        <module name="UnusedImports"/>
        <module name="LineLength"/>
        <module name="MethodLength"/>
        <module name="GenericWhitespace"/>
        <module name="WhitespaceAround"/>
        <module name="RedundantModifier"/>
        <module name="EmptyBlock"/>
        <module name="EmptyStatement"/>
        <module name="SimplifyBooleanExpression"/>
        <module name="SimplifyBooleanReturn"/>
        <module name="TodoComment"/>
        <module name="StringLiteralEquality"/>
        <module name="Indentation"/>
        <module name="OneStatementPerLine"/>
        <module name="CyclomaticComplexity"/>
        <module name="OuterTypeFilename"/>
        <module name="NestedForDepth">
            <property name="max" value="2"/>
        </module>
        <module name="NestedIfDepth">
            <property name="max" value="2"/>
        </module>
        <module name="HiddenField">
            <property name="ignoreConstructorParameter" value="true"/>
        </module>
        <module name="JavadocMethod">
            <property name="allowMissingPropertyJavadoc" value="true"/>
        </module>
        <module name="VisibilityModifier">
            <property name="protectedAllowed" value="true"/>
        </module>
    </module>
</module>
```
Lisätään aiemmin luotuun _nbactions.xml_-tiedostoon vielä yksi valikko jolla voi ajaa Checkstylen helposti suoraan Netbeansistä, lisää tiedostoon alla oleva pätkä. Tallenna ja aja projektille **Clean and Build**. Nyt pitäisi Custom valikossa näkyä Coberturan ja Pitin lisäksi Checkstyle.

```xml
<action>
  <actionName>CUSTOM-checkstyle</actionName>
  <displayName>Checkstyle</displayName>
  <goals>
    <goal>jxr:jxr</goal>
    <goal>checkstyle:checkstyle -Dcheckstyle.config.location=checkstyle.xml</goal>
  </goals>
</action>
```

Vaihtoehtoisesti Checkstylen voi ajaa komentoriviltä komennolla <code>mvn jxr:jxr checkstyle:checkstyle -Dcheckstyle.config.location=checkstyle.xml</code> Sekä komentoriviltä ajettaessa että suoraan Netbeansistä _checkstyle.xml_ on aiemmin luodun konfiguraatiotiedoston nimi ja komennot olettavat että tiedosto sijaitsee projektihakemiston juuressa.

Generoituasi Checkstyle raportin löydät sen polusta **/target/site/checkstyle.html**.

Lisää Checkstylestä voi lukea ohtun sivuilta [ohtun checkstyle osio](https://github.com/mluukkai/ohtu2014/blob/master/web/laskari3.md)
