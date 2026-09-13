# Repo-sync

`grammar-core` wordt als git subtree gespiegeld onder `shared/grammar-core/` in beide productrepo's.

## Enige schrijfrichting

1. Wijzig gedeelde canon in `grammar-core`.
2. Merge die PR.
3. Maak in ieder productrepo een syncbranch.
4. Voer uit:

```bash
git subtree pull --prefix=shared/grammar-core \
  https://github.com/Loumeister/grammar-core.git main --squash
```

5. Test het product en merge de sync-PR.

Wijzig nooit rechtstreeks bestanden onder `shared/grammar-core/`. Productafwijkingen horen in het lokale productcontract.

## Controle

Ieder productrepo moet in CI de canonieke mappen van de subtree vergelijken met `grammar-core/main`. De controle mag niets schrijven en geen PR openen. Zolang deze controle nog niet op de standaardbranch staat, vergelijkt de reviewer de subtree handmatig. Na een core-merge meldt de eerstvolgende controle drift totdat de subtree is bijgewerkt.

Een geïntegreerde package, plugin of monorepo is pas nodig als er werkelijk gedeelde runtimecode ontstaat.
