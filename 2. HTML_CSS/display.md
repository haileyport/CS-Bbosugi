## π Display

<br/>

### display μμ±μ΄λ ?

- μμμ λ΄λΆμ μΈλΆ λμ€νλ μ΄ μ νμ μ€μ νλ μμ±
  - μΈλΆ λμ€νλ μ΄ μ νμΌλ‘λ μμλ₯Ό νλ©΄μ μ΄λ»κ² λλ¬λκ² ν  κ²μΈμ§(block or Inline)μ λν λ°©λ²μ λνλ΄λ©°,
    λ΄λΆ λμ€νλ μ΄ μ νμΌλ‘λ μμμ λ μ΄μμ λ°©μ(flow, flex, grid)μ μ€μ νλ€.

<br/>

### display μ¬μ©νκΈ°

- `display` ν€μλ κ°μ μ΄μ©ν΄ λμ€νλ μ΄λ₯Ό μ§μ νλ€.

```jsx
.container {
	display : <display-keyword>;
}
```

<br/>

### Display μμ± λΆλ₯νκΈ°

<details markdown="1">
<summary>display μ νμ 6κ°μ§λ‘ λΆλ₯κ°λ₯νλ€ </summary>

- μΈλΆ λμ€νλ μ΄ μ ν
- λ΄λΆ λμ€νλ μ΄ μ ν
- λ¦¬μ€νΈ ν­λͺ©
- λ΄λΆμ©
- λ°μ€
- λ κ±°μ

</details>

<br/>

### βοΈΒ μΈλΆ λμ€νλ μ΄ μ ν(display-outside)

- μμμ μΈλΆ λμ€νλ μ΄ μ νμ μ€μ νλ ν€μλλ‘, νλ‘μ° λ μ΄μμμμ μμ μμ μ μ­ν κ³Ό κ°λ€.

  1οΈβ£Β `display : block;`

  - νλ¦μλ°λΌ μμΉν λΌμΈ μ μ²΄λ₯Ό μ°¨μ§νκ³ μ νλ μ±μ§μ κ°μ§λ μμ±
  - width μμ±μ λΆμ¬ν΄μ£Όλ©΄ λλΉλ§νΌ κ·Έ μμ­μ μ°¨μ§νλ€.
    ![block level elements](https://velog.velcdn.com/images/rachelyu1025/post/0b309cf4-6913-4371-bd96-3a0301e7aa12/image.png)

  2οΈβ£Β `display : inline;`

  - μ»¨νμΈ  λ§νΌμ ν¬κΈ°λ§ μ°¨μ§νλ μ±μ§μ κ°μ§ μμ±μΌλ‘, μμμ λ€μ μμλ μ°¨μ§ν  μ μλ κ³΅κ°μ΄ μλν κ°μ λΌμΈμ μμΉνλ€.
  - width, height, margin-top,margin-bottom μμ±μ΄ μ μ©λμ§ μλλ€.
    ![inline level elements](https://velog.velcdn.com/images/rachelyu1025/post/4a08e17b-82c3-46c8-97be-c509077ac36b/image.png)

π‘ μ νμ λ κ°μ μ§μνλ λΈλΌμ°μ λ ν€μλκ° block, inlineμΌλ‘ μ§μ  λμμ λ, λ΄λΆ μμλ€μ΄ νλ‘μ° λ μ΄μμμ μνλλ‘ μ€μ ν©λλ€.μ¦, μ΄λ€ μμλ₯Ό λΈλ‘μΌλ‘ μ§μ νλ©΄, ν΄λΉ μμμ μμμ΄ νλ‘μ° λ μ΄μμμ μ°Έμ¬νλ κ²μΌλ‘ κ°μ£Όνλ€.

<br/>

### βοΈΒ λ΄λΆ λμ€νλ μ΄ μ ν(display-inside)

- μμμ λ΄λΆ λμ€νλ μ΄ μ νμ μ€μ νλ ν€μλλ‘, λμ²΄ μμκ° μλ μμμ μ»¨νμΈ  μμ(formatting context)κ³Ό λ°°μΉ λ°©λ²μ λνλΈλ€.

π‘ μ»¨νμΈ  μμμ΄λ? https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flow_Layout/Intro_to_formatting_contexts

<br/>

1οΈβ£Β flow

β μΈλΆ λμ€νλ μ΄ μ νμ΄ inline λλ run-in μΌ κ²½μ°, μμμ μμμ΄ block λλ inline μ΄λΌλ©΄ inline boxλ₯Ό μμ±νλ©° μ΄μΈμ κ²½μ°, block boxλ₯Ό μμ±νλ€.

λ€λ₯Έ μμ±(position, float, overflow λ±..)μ κ°κ³Ό μμ μμ²΄κ° block λλ Inline μΈμ§μ λ°λΌ μ block formatting context(BFC)λ₯Ό μ€μ νκ±°λ μ½νμΈ λ₯Ό μμ μμμ ν΅ν©νλ€.

π‘Β BFC(Blcok Formatting Context)κ° λ­μ£ ?

- μΉνμ΄μ§μ λνλμλ blockλ€μ΄ λ³΄μ¬μ§λ CSS λ λλ§μ μΌλΆ

- μμμ BFCλ₯Ό μ μ©νλ©΄ νμ μμλ₯Ό λμμΌλ‘ ν λλ¦½μ μΈ λ μ΄μμ νκ²½μ λ§λ€ μ μκ³  λ€λ₯Έ μ£Όλ³ μμμλ λ μ΄μμ κ΄κ³λ₯Ό νμ±ν  μ μλ€.

  β blockμ μμ±μ΄ λ€μ λΆμ¬λμ΄ λ€λ₯΄κ² λ λλ§ λλ νμ λλ μ»¨νμΈ λ‘ block μ»¨νμΈ μ μμ λͺ¨λΈμ μλ―Ένλ€.

<details markdown="2">
  <summary> BFC μ‘°κ±΄ (νλλΌλ ν¬ν¨νλ μμλ€μ λͺ¨λ BFCλΌκ³  ν  μ μλ€.) </summary>

- λ¬Έμμ λ£¨νΈ μμ(`<html>`)μΌ λ

- νλ‘ν(Floating) λμμ λ β floatμ΄ noneμ΄ μλ κ²½μ°

- [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) μμ±μ΄Β absoluteΒ λλΒ fixedλ‘ μ μ©λ κ²½μ°

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β inline-blockμΌλ‘ μ μ©λ κ²½μ°

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β table-cell, HTML ν μΉΈμ κΈ°λ³Έκ°μΈ κ²½μ°

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β table-caption, HTML ν μ£Όμμ κΈ°λ³Έκ°μΈ κ²½μ°

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β table,Β table-row,Β table-row-group,Β table-header-group,Β table-footer-groupΒ (HTML νμμ, κ°κ° ν μ μ²΄, ν, λ³Έλ¬Έ, ν€λ, νΈν°μ κΈ°λ³Έκ°) λλΒ inline-tableμΈ μμκ° μμμ μΌλ‘ μμ±ν λ¬΄λͺ μΉΈ.

- [overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow)κ°Β visibleμ΄ μλ λΈλ‘ μμμΈ κ²½μ°

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β flow-root.

- [contain](https://developer.mozilla.org/ko/docs/Web/CSS/contain)μ΄Β layout,Β content,Β paint.

- μ€μ€λ‘ νλ μ€, κ·Έλ¦¬λ, νμ΄λΈ μ»¨νμ΄λκ° μλ κ²½μ°μ νλ μ€ ν­λͺ©([display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β flexΒ λλΒ inline-flexμΈ μμμ λ°λ‘ μλ μμ)

- μ€μ€λ‘ νλ μ€, κ·Έλ¦¬λ, νμ΄λΈ μ»¨νμ΄λκ° μλ κ²½μ°μ κ·Έλ¦¬λ ν­λͺ©([display](https://developer.mozilla.org/ko/docs/Web/CSS/display)κ°Β gridΒ λλΒ inline-gridμΈ μμμ λ°λ‘ μλ μμ)

- λ€μ΄ μ»¨νμ΄λ([column-count](https://developer.mozilla.org/ko/docs/Web/CSS/column-count)Β λλ ([column-width](https://developer.mozilla.org/ko/docs/Web/CSS/column-width)κ°Β autoκ° μλ κ²½μ°.Β column-count: 1Β ν¬ν¨).

- [column-span](https://developer.mozilla.org/ko/docs/Web/CSS/column-span)μ΄Β allμΈ κ²½μ°. ν΄λΉνλ μμκ° λ€μ΄ μ»¨νμ΄λ μμ μμΉνμ§ μμλ ν­μ μλ‘μ΄ λΈλ‘ μμ λ§₯λ½μ μμ±ν΄μΌ ν©λλ€.

</details>

<br/>

2οΈβ£Β flow-root

β μμλ μμ λ£¨νΈκ° μλ μμΉλ₯Ό μ μνλ μ BFCλ₯Ό μ€μ νλ block boxλ₯Ό μμ±νλ€.

3οΈβ£Β table

β HTML μμ(`<table>`) μ²λΌ μλνλ©°, block λ λ²¨μ΄λ€.

4οΈβ£Β flex

β block μμ μ²λΌ μλνλ©°, flexbox modelμ λ°λΌ λ°°μΉλλ€.

5οΈβ£Β grid

β block μμ μ²λΌ μλνλ©°, grid moedelμ λ°λΌ λ°°μΉλλ€.

π‘Β display: flex λλ display: grid κ° μ§μ λ κ²½μ°μ κ°μ΄ λ΄λΆ κ°λ§μ μ°Ύμ λ, μμλ€μ μΈλΆ λμ€νλ μ΄ μ νμ blockμ΄ λκΈ° λλ¬Έμ flex λλ grid μ»¨νμ΄λμ μμ±λ box λ€μ΄ block levelμ κ°μ§ κ²μ μμν  μ μλ€.

6οΈβ£Β ruby

β inline μμ μ²λΌ μλνλ©°, ruby formatting modelμ λ°λΌ λ°°μΉλλ€.

HTML μμ(`<ruby>`) μ²λΌ μλνλ€.

![ruby μμ±](https://velog.velcdn.com/images/rachelyu1025/post/7b4eb34b-3dc5-45f1-95fe-da3178978a1a/image.png)

<br/>

### π€Β λ°μ€ (`<display-box>`)

- μμκ° λμ€νλ μ΄ λ°μ€λ₯Ό μμ±ν΄μΌ νλμ§λ₯Ό μ€μ 

  1οΈβ£Β contents
  β μμ μμ²΄ λ°μ€λ₯Ό μμ±νμ§ μκ³ , μμμ μμλ€μ΄ μμ±ν λ°μ€λ‘ λμ²΄νλ€.

  2οΈβ£Β none
  β μμκ° λ μ΄μμμ μν₯μ μ£Όμ§ λͺ»νλλ‘ μ€μ νλ€(= μμκ° μμ μ‘΄μ¬νμ§ μλ κ²μ²λΌ λ λλ§)
  `display : none;` μμμ λͺ¨λ  μμ μμλ λ³΄μ΄μ§ μλ€.

  π‘Β μμκ° λ³΄μ΄μ§ μμμΌνμ§λ§, λ μ΄μμμ μ°Έμ¬ν΄ μμ μ κ³΅κ°μ μ°¨μ§ν΄μΌνλ€λ©΄?

  => `visibility: visible | hidden | collapse` μμ±μ μ΄μ©ν  μ μλ€.

<br/>

### π‘Β λ κ±°μ (`display : inline-block` )

- μμκ° block levelμ boxλ₯Ό μμ±νμ§λ§, λ§μΉ νλμ μΈλΌμΈ λ°μ€μ²λΌ μ£Όλ³ μ»¨νμΈ μ ν¨κ» flow λ μ΄μμμ νλ¦μ μ°Έμ¬νλ€. (inline flow-rootμ κ°λ€.)

  => μ½κ² inline μμ±κ³Ό block μμ±μ΄ ν©μ³μ§ μμ±μΌλ‘ μ΄ν΄ν  μ μλ€.

- κΈ°λ³Έμ μΌλ‘λ inline μμ±μ μ§λμ§λ§, μμλ‘ ν¬κΈ°λ₯Ό λ°κΏμ€ μ μλ€.

<br/>

β¨ Reference

- [MDN Display](https://developer.mozilla.org/ko/docs/Web/CSS/display)

- [CSS display μ ν ](https://sorto.me/docs/Web/CSS/display)
- [BFC](http://www.devdic.com/css/reference/documents/document:1971/%EB%B8%94%EB%A1%9D-%EC%96%91%EC%8B%9D%ED%99%94-%EB%AC%B8%EB%A7%A5)
- [css ruby](https://www.w3.org/TR/css-ruby-1/#ruby-def)
