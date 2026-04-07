
# Kérdések
- vannak olyanok, ahol csak egyetlen timeframe-re van label. azok valszeg véletlenek

# Hipotézisek
- Az ASD és ADHDs gyerkeknél rosszabb a koordináció (rt mean square, kilengési amplitúdó, szórás)
- Kilengési amplitúdó, átlag és szórás. A pszichomotorikum, többletmozgások. - tehát ha többet mozog, hiperaktív, 
- többletmozgás
- gyorsabb mozgás
- a játékos feladatok (állatmozgások)-nál nagyobb a szögsebesség variablitás, mindennapi 

# Variables



|              |                                                                                                                                                                                                                            |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id           | A UNIX timeframe, ami minden fájlnévben szerepel. Ez egy becsült érték, ami a felvétel indítását jelöli. (Van kis diszkrepancia az indítás és a tényleges mérés indulása közöt. Ezt a UNIX time-ot használom szinkronhoz.) |
| kid_id       | A gyerekek egyedi azonosítója.                                                                                                                                                                                             |
| solomon_file | Ez a kódolt fájlok töve (tehát a fájlnév a .csv kiterjesztés nélkül). Egységes szerekezetre van hozva. Mindig `<id>_<action>_<kid_id>` formátumban szerepel.                                                               |
|              |                                                                                                                                                                                                                            |
| group_label  | adhd (ad), autizmus (au), neurotipikus (nt)                                                                                                                                                                                |
|              |                                                                                                                                                                                                                            |
| action       | A mozgástípus, ami a solomon fájlnevekben is szerepel.                                                                                                                                                                     |
| action_label | Ami a kódolt solomon outputokban szerepel címkeként az adott időbélyegeknél.                                                                                                                                               |
|              |                                                                                                                                                                                                                            |

# Preproc

- szegmentáció az egész szekvenciára
- mozgó ablakokkal felszabdalni (1 sec? hop length? és ahol nincs annyi?)
# Features

- standardok: mean, std, variance, min, max, stb. 
- attemptek? indikatív lehet?
- feature-ök mozgó ablakokon (vagy preprocban, vagy featurönként)
- sekély ML-hez van pár extra feature extraction

| Feature                       | Formula                                                    | Interpretation                                | Inference                                                                                                                                      |
| ----------------------------- | ---------------------------------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Mean                          | $$\mu = \frac{1}{N}\sum_{i=1}^{N} x_i$$                    | Average signal value in window                | **acc:** baseline movement bias or sustained directional motion; **gyro:** persistent rotation tendency; **grav:** wrist orientation / posture |
| Std                           | $$\sigma = \sqrt{\frac{1}{N}\sum (x_i-\mu)^2}$$            | Spread of signal around mean                  | **acc:** movement variability / restlessness; **gyro:** rotational instability; **grav:** orientation instability                              |
| Variance                      | $$\frac{1}{N}\sum (x_i-\mu)^2$$                            | Magnitude variability                         | **acc:** amplitude variability / hyperactivity; **gyro:** rapid directional changes; **grav:** posture variation                               |
| Min                           | $$\min(x)$$                                                | Lowest signal value                           | **acc:** abrupt negative acceleration; **gyro:** extreme reverse rotation                                                                      |
| Max                           | $$\max(x)$$                                                | Highest signal value                          | **acc:** peak acceleration / impulse; **gyro:** peak rotation speed                                                                            |
| Peak-to-Peak                  | $$\max(x)-\min(x)$$                                        | Full amplitude range                          | **acc:** strength/intensity of movement; **gyro:** range of wrist rotation                                                                     |
| Zero Crossing Rate            | $$ZCR=N−11​∑i=1N−1​1{xi​⋅xi+1​<0}$$                        |                                               |                                                                                                                                                |
| Energy                        | $$E=\sum x_i^2$$ or $$E=\frac{1}{N}\sum x_i^2$$            | Total signal power                            | **acc:** overall movement intensity; **gyro:** overall rotational activity                                                                     |
| Signal Magnitude              | $$v=\sqrt{x^2+y^2+z^2}$$                                   |                                               |                                                                                                                                                |
| Jerk                          | $$jerk = \frac{da}{dt}$$                                   | Rate of change of acceleration                | **acc:** movement smoothness / abruptness; high jerk indicates sudden or poorly controlled motion                                              |
| Spectral Entropy              | $$H=-\sum p(f)\log p(f)$$                                  | Distribution uniformity of frequency spectrum | **acc:** irregular or chaotic motion patterns; **gyro:** irregular rotational movement                                                         |
| Dominant Frequency (FFT peak) | $$fpeak​=argmaxf​∣FFT(x)∣x$$                               | FFT                                           | **acc:** dominant rhythm of repetitive movement (e.g., tapping, flapping); **gyro:** dominant rotational oscillation frequency.                |
| Angular Velocity Magnitude    | $$∣ω∣=ωx2​+ωy2​+ωz2​​$$                                    |                                               |                                                                                                                                                |
| Tilt Angle Change             | $$θ=arccos(gx2​+gy2​+gz2​​gz​​)$$ or<br>$$Δθ=∣θt+1​−θt​∣$$ | Change in orientation relative to gravity     | **grav:** posture shifts of wrist; instability or large orientation adjustments                                                                |
| Path Length                   | $$L=\sum \|v_i\|\Delta t$$                                 | Estimated cumulative movement distance        | **acc:** total movement trajectory / movement amount                                                                                           |
| Fragments                     | $$count(\text{motion segments})$$                          | Number of detected attempts during task       | Indicates retries, hesitation, fragmented motor execution during task completion                                                               |

# Meeting notes 03.05

- ahol több címke van egy mozgásnál (action), ott az elsőt kell alapul venni. 
- nem számít, hogy hány egységben csinálta a gyerek, mert az csak annyi, hogy kérte, hogy csinálja meg újra
- valahogy elmagyarázni, miért jobb a csúszóablak, mint egy mozgást aggregálni egyben úgy, ahogy van. 
- átlagoljuk a tengelyeket vagy ne? és ha igen, mikor? feature előtt vagy után? (hajlok a feature utánra)
- miből lehet nézni koordinációt, impulzivitást, sebességet, többletmozgást (hiperaktivitást)


```
// Use DBML to define your database structure

// Docs: https://dbml.dbdiagram.io/docs

  

//Table follows {

following_user_id integer

followed_user_id integer

created_at timestamp

}

  

//Table users {

id integer [primary key]

username varchar

role varchar

created_at timestamp

}

  

Table posts {

id integer [primary key]

title varchar

body text [note: 'Content of the post']

user_id integer [not null]

status varchar

created_at timestamp

}

  

Ref user_posts: posts.user_id > users.id // many-to-one

  

Ref: users.id < follows.following_user_id

  

Ref: users.id < follows.followed_user_id
```