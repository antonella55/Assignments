Using code from tuesday... Diversity through time

    library(paleotree)

    ## Loading required package: ape

    library(paleobioDB)

    ## Loading required package: raster

    ## Loading required package: sp

    ## 
    ## Attaching package: 'raster'

    ## The following objects are masked from 'package:ape':
    ## 
    ##     rotate, zoom

    ## Loading required package: maps

    data(graptPBDB)
    head(graptOccPBDB)

    ##   occurrence_no record_type reid_no obsolete collection_no
    ## 1          1669  occurrence      NA       NA           215
    ## 2          2186  occurrence      NA       NA           256
    ## 3          2216  occurrence      NA       NA           258
    ## 4          2217  occurrence      NA       NA           258
    ## 5          2318  occurrence      NA       NA           270
    ## 6          2319  occurrence      NA       NA           270
    ##      identified_name identified_rank identified_no taxonomic_reason
    ## 1  Chaunograptus sp.           genus         33800                 
    ## 2  Dendrograptus sp.           genus         33551                 
    ## 3 Acanthograptus sp.           genus         33536                 
    ## 4  Dendrograptus sp.           genus         33551                 
    ## 5  Dendrograptus sp.           genus         33551                 
    ## 6   Hallograptus sp.           genus         33673                 
    ##    accepted_name accepted_rank accepted_no early_interval late_interval
    ## 1  Chaunograptus         genus       33800      St Davids     St Davids
    ## 2  Dendrograptus         genus       33551  Trempealeauan Trempealeauan
    ## 3 Acanthograptus         genus       33536       Cambrian      Cambrian
    ## 4  Dendrograptus         genus       33551       Cambrian      Cambrian
    ## 5  Dendrograptus         genus       33551       Tremadoc      Tremadoc
    ## 6   Hallograptus         genus       33673       Tremadoc      Tremadoc
    ##   early_age late_age reference_no   primary_name primary_reso
    ## 1     513.0    501.0           13  Chaunograptus             
    ## 2     501.0    485.4           13  Dendrograptus             
    ## 3     541.0    485.4           13 Acanthograptus             
    ## 4     541.0    485.4           13  Dendrograptus             
    ## 5     485.4    477.7           13  Dendrograptus             
    ## 6     485.4    477.7           13   Hallograptus             
    ##   subgenus_name subgenus_reso species_name species_reso subgenus
    ## 1                                      sp.                    NA
    ## 2                                      sp.                    NA
    ## 3                                      sp.                    NA
    ## 4                                      sp.                    NA
    ## 5                                      sp.                    NA
    ## 6                                      sp.                    NA
    ##   subgenus_no          genus genus_no family family_no        order
    ## 1          NA  Chaunograptus    33800               NA             
    ## 2          NA  Dendrograptus    33551               NA   Dendroidea
    ## 3          NA Acanthograptus    33536               NA   Dendroidea
    ## 4          NA  Dendrograptus    33551               NA   Dendroidea
    ## 5          NA  Dendrograptus    33551               NA   Dendroidea
    ## 6          NA   Hallograptus    33673               NA Graptoloidea
    ##   order_no         class class_no       phylum phylum_no   authorizer
    ## 1       NA Graptolithina    33534 Hemichordata     33518 Sepkoski, J.
    ## 2    33535 Graptolithina    33534 Hemichordata     33518 Sepkoski, J.
    ## 3    33535 Graptolithina    33534 Hemichordata     33518 Sepkoski, J.
    ## 4    33535 Graptolithina    33534 Hemichordata     33518 Sepkoski, J.
    ## 5    33535 Graptolithina    33534 Hemichordata     33518 Sepkoski, J.
    ## 6    33606 Graptolithina    33534 Hemichordata     33518 Sepkoski, J.
    ##       enterer modifier
    ## 1 Sommers, M.  unknown
    ## 2 Sommers, M.  unknown
    ## 3 Sommers, M.  unknown
    ## 4 Sommers, M.  unknown
    ## 5 Sommers, M.  unknown
    ## 6 Sommers, M.  unknown

    occSpecies<-taxonSortPBDBocc(graptOccPBDB, rank="species")
    head(occSpecies)

    ## $`Adelograptus antiquus`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 3609        596430  occurrence      NA       NA         63189
    ## 3612        596434  occurrence      NA       NA         63190
    ## 3627        596451  occurrence      NA       NA         63192
    ## 3630        596454  occurrence      NA       NA         63194
    ## 3632        596458  occurrence      NA       NA         63195
    ## 3667        596498  occurrence      NA       NA         63204
    ## 4223        826761  occurrence      NA       NA         91172
    ##              identified_name identified_rank identified_no
    ## 3609 Adelograptus ? antiquus         species         84007
    ## 3612 Adelograptus ? antiquus         species         84007
    ## 3627 Adelograptus ? antiquus         species         84007
    ## 3630 Adelograptus ? antiquus         species         84007
    ## 3632 Adelograptus ? antiquus         species         84007
    ## 3667 Adelograptus ? antiquus         species         84007
    ## 4223   Adelograptus antiquus         species         84007
    ##      taxonomic_reason         accepted_name accepted_rank accepted_no
    ## 3609             <NA> Adelograptus antiquus       species       84007
    ## 3612             <NA> Adelograptus antiquus       species       84007
    ## 3627             <NA> Adelograptus antiquus       species       84007
    ## 3630             <NA> Adelograptus antiquus       species       84007
    ## 3632             <NA> Adelograptus antiquus       species       84007
    ## 3667             <NA> Adelograptus antiquus       species       84007
    ## 4223             <NA> Adelograptus antiquus       species       84007
    ##      early_interval late_interval early_age late_age reference_no
    ## 3609    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 3612  Lancefieldian   Bendigonian     485.4    473.9        18179
    ## 3627  Lancefieldian   Bendigonian     485.4    473.9        18179
    ## 3630    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 3632    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 3667    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 4223        Ibexian       Ibexian     488.3    471.8        24434
    ##      primary_name primary_reso subgenus_name subgenus_reso species_name
    ## 3609 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3612 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3627 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3630 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3632 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3667 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 4223 Adelograptus         <NA>          <NA>          <NA>     antiquus
    ##      species_reso subgenus subgenus_no        genus genus_no family
    ## 3609         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3612         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3627         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3630         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3632         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3667         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 4223         <NA>       NA          NA Adelograptus    33537   <NA>
    ##      family_no      order order_no         class class_no       phylum
    ## 3609        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3612        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3627        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3630        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3632        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3667        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 4223        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ##      phylum_no  authorizer     enterer  modifier
    ## 3609     33518   Hendy, A.   Hendy, A. Hendy, A.
    ## 3612     33518   Hendy, A.   Hendy, A.   unknown
    ## 3627     33518   Hendy, A.   Hendy, A.   unknown
    ## 3630     33518   Hendy, A.   Hendy, A. Hendy, A.
    ## 3632     33518   Hendy, A.   Hendy, A.   unknown
    ## 3667     33518   Hendy, A.   Hendy, A.   unknown
    ## 4223     33518 Villier, L. Villier, L.   unknown
    ## 
    ## $`Adelograptus clarki`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 3610        596431  occurrence      NA       NA         63189
    ## 3633        596459  occurrence      NA       NA         63195
    ##          identified_name identified_rank identified_no taxonomic_reason
    ## 3610 Adelograptus clarki         species         84009             <NA>
    ## 3633 Adelograptus clarki         species         84009             <NA>
    ##            accepted_name accepted_rank accepted_no early_interval
    ## 3610 Adelograptus clarki       species       84009    Tremadocian
    ## 3633 Adelograptus clarki       species       84009    Tremadocian
    ##      late_interval early_age late_age reference_no primary_name
    ## 3610   Tremadocian     485.4    477.7        18179 Adelograptus
    ## 3633   Tremadocian     485.4    477.7        18179 Adelograptus
    ##      primary_reso subgenus_name subgenus_reso species_name species_reso
    ## 3610         <NA>          <NA>          <NA>       clarki         <NA>
    ## 3633         <NA>          <NA>          <NA>       clarki         <NA>
    ##      subgenus subgenus_no        genus genus_no family family_no
    ## 3610       NA          NA Adelograptus    33537   <NA>        NA
    ## 3633       NA          NA Adelograptus    33537   <NA>        NA
    ##           order order_no         class class_no       phylum phylum_no
    ## 3610 Dendroidea    33535 Graptolithina    33534 Hemichordata     33518
    ## 3633 Dendroidea    33535 Graptolithina    33534 Hemichordata     33518
    ##      authorizer   enterer  modifier
    ## 3610  Hendy, A. Hendy, A. Hendy, A.
    ## 3633  Hendy, A. Hendy, A.   unknown
    ## 
    ## $`Amplexograptus rugosus`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 5893       1256955  occurrence      NA       NA        166800
    ##             identified_name identified_rank identified_no taxonomic_reason
    ## 5893 Amplexograptus rugosus         species        315895             <NA>
    ##               accepted_name accepted_rank accepted_no early_interval
    ## 5893 Amplexograptus rugosus       species      315895    Longvillian
    ##      late_interval early_age late_age reference_no   primary_name
    ## 5893 Marshbrookian     457.5      452          102 Amplexograptus
    ##      primary_reso subgenus_name subgenus_reso species_name species_reso
    ## 5893         <NA>          <NA>          <NA>      rugosus         <NA>
    ##      subgenus subgenus_no          genus genus_no family family_no
    ## 5893       NA          NA Amplexograptus    33615   <NA>        NA
    ##             order order_no         class class_no       phylum phylum_no
    ## 5893 Graptoloidea    33606 Graptolithina    33534 Hemichordata     33518
    ##      authorizer    enterer modifier
    ## 5893 Wagner, P. Wagner, P.  unknown
    ## 
    ## $`Azygograptus novozealandicus`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 3898        601800  occurrence      NA       NA         63967
    ## 3960        601885  occurrence      NA       NA         63960
    ## 3964        601889  occurrence      NA       NA         63961
    ## 3993        601921  occurrence      NA       NA         63963
    ## 4014        601945  occurrence      NA       NA         63965
    ##                          identified_name identified_rank identified_no
    ## 3898        Azygograptus novozealandicus         species         84630
    ## 3960        Azygograptus novozealandicus         species         84630
    ## 3964        Azygograptus novozealandicus         species         84630
    ## 3993 Azygograptus novozealandicus n. sp.         species         84630
    ## 4014        Azygograptus novozealandicus         species         84630
    ##      taxonomic_reason                accepted_name accepted_rank
    ## 3898             <NA> Azygograptus novozealandicus       species
    ## 3960             <NA> Azygograptus novozealandicus       species
    ## 3964             <NA> Azygograptus novozealandicus       species
    ## 3993             <NA> Azygograptus novozealandicus       species
    ## 4014             <NA> Azygograptus novozealandicus       species
    ##      accepted_no early_interval late_interval early_age late_age
    ## 3898       84630     Gisbornian    Gisbornian     460.9    456.1
    ## 3960       84630     Gisbornian    Gisbornian     460.9    456.1
    ## 3964       84630     Gisbornian    Gisbornian     460.9    456.1
    ## 3993       84630    Darriwilian   Darriwilian     467.3    458.4
    ## 4014       84630     Gisbornian    Gisbornian     460.9    456.1
    ##      reference_no primary_name primary_reso subgenus_name subgenus_reso
    ## 3898        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 3960        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 3964        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 3993        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 4014        18428 Azygograptus         <NA>          <NA>          <NA>
    ##         species_name species_reso subgenus subgenus_no        genus
    ## 3898 novozealandicus         <NA>       NA          NA Azygograptus
    ## 3960 novozealandicus         <NA>       NA          NA Azygograptus
    ## 3964 novozealandicus         <NA>       NA          NA Azygograptus
    ## 3993 novozealandicus       n. sp.       NA          NA Azygograptus
    ## 4014 novozealandicus         <NA>       NA          NA Azygograptus
    ##      genus_no family family_no        order order_no         class
    ## 3898    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 3960    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 3964    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 3993    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 4014    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ##      class_no       phylum phylum_no authorizer   enterer modifier
    ## 3898    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 3960    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 3964    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 3993    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 4014    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 
    ## $`Climacograptus bicornis`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 2399        246238  occurrence      NA       NA         24117
    ## 4166        748935  occurrence      NA       NA         80104
    ## 4320        955088  occurrence      NA       NA        111711
    ## 4325        955095  occurrence      NA       NA        111713
    ## 4332        955103  occurrence      NA       NA        111718
    ## 4516        996584  occurrence      NA       NA        120528
    ## 4685       1139721  occurrence      NA       NA        145233
    ## 4695       1139731  occurrence      NA       NA        145236
    ## 4703       1139741  occurrence      NA       NA        145237
    ## 4713       1139751  occurrence      NA       NA        145238
    ## 4725       1139763  occurrence      NA       NA        145240
    ## 4773       1141828  occurrence      NA       NA        145463
    ## 4774       1141829  occurrence      NA       NA        145464
    ## 5330       1144012  occurrence      NA       NA        145615
    ##              identified_name identified_rank identified_no
    ## 2399 Climacograptus bicornis         species        306375
    ## 4166 Climacograptus bicornis         species        306375
    ## 4320 Climacograptus bicornis         species        306375
    ## 4325 Climacograptus bicornis         species        306375
    ## 4332 Climacograptus bicornis         species        306375
    ## 4516 Climacograptus bicornis         species        306375
    ## 4685 Climacograptus bicornis         species        306375
    ## 4695 Climacograptus bicornis         species        306375
    ## 4703 Climacograptus bicornis         species        306375
    ## 4713 Climacograptus bicornis         species        306375
    ## 4725 Climacograptus bicornis         species        306375
    ## 4773 Climacograptus bicornis         species        306375
    ## 4774 Climacograptus bicornis         species        306375
    ## 5330 Climacograptus bicornis         species        306375
    ##      taxonomic_reason           accepted_name accepted_rank accepted_no
    ## 2399             <NA> Climacograptus bicornis       species      306375
    ## 4166             <NA> Climacograptus bicornis       species      306375
    ## 4320             <NA> Climacograptus bicornis       species      306375
    ## 4325             <NA> Climacograptus bicornis       species      306375
    ## 4332             <NA> Climacograptus bicornis       species      306375
    ## 4516             <NA> Climacograptus bicornis       species      306375
    ## 4685             <NA> Climacograptus bicornis       species      306375
    ## 4695             <NA> Climacograptus bicornis       species      306375
    ## 4703             <NA> Climacograptus bicornis       species      306375
    ## 4713             <NA> Climacograptus bicornis       species      306375
    ## 4725             <NA> Climacograptus bicornis       species      306375
    ## 4773             <NA> Climacograptus bicornis       species      306375
    ## 4774             <NA> Climacograptus bicornis       species      306375
    ## 5330             <NA> Climacograptus bicornis       species      306375
    ##       early_interval   late_interval early_age late_age reference_no
    ## 2399      Trentonian     Richmondian     460.9    443.7         6817
    ## 4166         Idavere         Idavere     460.9    455.8        26936
    ## 4320 Late Ordovician Late Ordovician     458.4    443.4        36540
    ## 4325 Late Ordovician Late Ordovician     458.4    443.4        36540
    ## 4332 Late Ordovician Late Ordovician     458.4    443.4        36540
    ## 4516        Sandbian        Sandbian     458.4    453.0        38521
    ## 4685      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4695      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4703      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4713      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4725      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4773       Eastonian       Eastonian     456.1    449.5        46966
    ## 4774       Eastonian       Eastonian     456.1    449.5        46966
    ## 5330      Caradocian      Caradocian     460.9    449.5        47089
    ##        primary_name primary_reso subgenus_name subgenus_reso species_name
    ## 2399 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4166 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4320 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4325 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4332 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4516 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4685 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4695 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4703 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4713 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4725 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4773 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4774 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 5330 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ##      species_reso subgenus subgenus_no          genus genus_no
    ## 2399         <NA>       NA          NA Climacograptus    33636
    ## 4166         <NA>       NA          NA Climacograptus    33636
    ## 4320         <NA>       NA          NA Climacograptus    33636
    ## 4325         <NA>       NA          NA Climacograptus    33636
    ## 4332         <NA>       NA          NA Climacograptus    33636
    ## 4516         <NA>       NA          NA Climacograptus    33636
    ## 4685         <NA>       NA          NA Climacograptus    33636
    ## 4695         <NA>       NA          NA Climacograptus    33636
    ## 4703         <NA>       NA          NA Climacograptus    33636
    ## 4713         <NA>       NA          NA Climacograptus    33636
    ## 4725         <NA>       NA          NA Climacograptus    33636
    ## 4773         <NA>       NA          NA Climacograptus    33636
    ## 4774         <NA>       NA          NA Climacograptus    33636
    ## 5330         <NA>       NA          NA Climacograptus    33636
    ##              family family_no        order order_no         class class_no
    ## 2399 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4166 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4320 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4325 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4332 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4516 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4685 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4695 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4703 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4713 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4725 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4773 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4774 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5330 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ##            phylum phylum_no           authorizer    enterer   modifier
    ## 2399 Hemichordata     33518          Holland, S. Hanson, T.    unknown
    ## 4166 Hemichordata     33518 Novack-Gottshall, P.  Hearn, P. Wagner, P.
    ## 4320 Hemichordata     33518           Miller, A.  Kolbe, S.  Kolbe, S.
    ## 4325 Hemichordata     33518           Miller, A.  Kolbe, S.    unknown
    ## 4332 Hemichordata     33518           Miller, A.  Kolbe, S.    unknown
    ## 4516 Hemichordata     33518        Kiessling, W. Merkel, U.    unknown
    ## 4685 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4695 Hemichordata     33518        Kiessling, W. Krause, M. Krause, M.
    ## 4703 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4713 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4725 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4773 Hemichordata     33518        Kiessling, W. Krause, M. Krause, M.
    ## 4774 Hemichordata     33518        Kiessling, W. Krause, M. Krause, M.
    ## 5330 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 
    ## $`Climacograptus scalaris`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 233          41894  occurrence      NA       NA          3281
    ## 236          41899  occurrence      NA       NA          3282
    ## 2530        260374  occurrence      NA       NA         25168
    ## 2884        285928  occurrence      NA       NA         27197
    ## 2948        287240  occurrence      NA       NA         27388
    ## 3173        291182  occurrence      NA       NA         27782
    ## 3246        292390  occurrence      NA       NA         27838
    ## 5115       1143763  occurrence      NA       NA        145587
    ## 5122       1143780  occurrence      NA       NA        145589
    ## 5132       1143790  occurrence      NA       NA        145590
    ## 5154       1143812  occurrence      NA       NA        145591
    ## 5204       1143865  occurrence      NA       NA        145598
    ## 5344       1144116  occurrence      NA       NA        145653
    ## 5355       1144128  occurrence      NA       NA        145654
    ## 5365       1144142  occurrence      NA       NA        145655
    ## 5385       1144162  occurrence      NA       NA        145656
    ## 5871       1218886  occurrence      NA       NA        159343
    ## 5896       1257991  occurrence      NA       NA        166909
    ##                identified_name identified_rank identified_no
    ## 233    Climacograptus scalaris         species        316364
    ## 236    Climacograptus scalaris         species        316364
    ## 2530   Climacograptus scalaris         species        316364
    ## 2884   Climacograptus scalaris         species        316364
    ## 2948   Climacograptus scalaris         species        316364
    ## 3173   Climacograptus scalaris         species        316364
    ## 3246   Climacograptus scalaris         species        316364
    ## 5115   Climacograptus scalaris         species        316364
    ## 5122 Climacograptus ? scalaris         species        316364
    ## 5132   Climacograptus scalaris         species        316364
    ## 5154   Climacograptus scalaris         species        316364
    ## 5204   Climacograptus scalaris         species        316364
    ## 5344   Climacograptus scalaris         species        316364
    ## 5355   Climacograptus scalaris         species        316364
    ## 5365   Climacograptus scalaris         species        316364
    ## 5385   Climacograptus scalaris         species        316364
    ## 5871   Climacograptus scalaris         species        316364
    ## 5896   Climacograptus scalaris         species        316364
    ##      taxonomic_reason           accepted_name accepted_rank accepted_no
    ## 233              <NA> Climacograptus scalaris       species      316364
    ## 236              <NA> Climacograptus scalaris       species      316364
    ## 2530             <NA> Climacograptus scalaris       species      316364
    ## 2884             <NA> Climacograptus scalaris       species      316364
    ## 2948             <NA> Climacograptus scalaris       species      316364
    ## 3173             <NA> Climacograptus scalaris       species      316364
    ## 3246             <NA> Climacograptus scalaris       species      316364
    ## 5115             <NA> Climacograptus scalaris       species      316364
    ## 5122             <NA> Climacograptus scalaris       species      316364
    ## 5132             <NA> Climacograptus scalaris       species      316364
    ## 5154             <NA> Climacograptus scalaris       species      316364
    ## 5204             <NA> Climacograptus scalaris       species      316364
    ## 5344             <NA> Climacograptus scalaris       species      316364
    ## 5355             <NA> Climacograptus scalaris       species      316364
    ## 5365             <NA> Climacograptus scalaris       species      316364
    ## 5385             <NA> Climacograptus scalaris       species      316364
    ## 5871             <NA> Climacograptus scalaris       species      316364
    ## 5896             <NA> Climacograptus scalaris       species      316364
    ##      early_interval late_interval early_age late_age reference_no
    ## 233        Aeronian      Aeronian     440.8    438.5          155
    ## 236        Aeronian      Aeronian     440.8    438.5          155
    ## 2530    Alexandrian   Alexandrian     443.4    436.0         7063
    ## 2884     Llandovery    Llandovery     443.4    433.4         7455
    ## 2948     Rhuddanian    Rhuddanian     443.4    440.8         7455
    ## 3173     Llandovery    Llandovery     443.4    433.4         7624
    ## 3246     Llandovery    Llandovery     443.4    433.4         7624
    ## 5115     Llandovery    Llandovery     443.4    433.4        47076
    ## 5122     Llandovery    Llandovery     443.4    433.4        47076
    ## 5132     Llandovery    Llandovery     443.4    433.4        47076
    ## 5154     Llandovery    Llandovery     443.4    433.4        47076
    ## 5204     Llandovery    Llandovery     443.4    433.4        47083
    ## 5344     Rhuddanian    Rhuddanian     443.4    440.8        47103
    ## 5355     Rhuddanian    Rhuddanian     443.4    440.8        47103
    ## 5365       Aeronian      Aeronian     440.8    438.5        47103
    ## 5385       Aeronian      Aeronian     440.8    438.5        47103
    ## 5871       Aeronian      Aeronian     440.8    438.5        52096
    ## 5896      Bolindian     Bolindian     449.5    443.7           78
    ##        primary_name primary_reso subgenus_name subgenus_reso species_name
    ## 233  Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 236  Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 2530 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 2884 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 2948 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 3173 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 3246 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5115 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5122 Climacograptus            ?          <NA>          <NA>     scalaris
    ## 5132 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5154 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5204 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5344 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5355 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5365 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5385 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5871 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5896 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ##      species_reso subgenus subgenus_no          genus genus_no
    ## 233          <NA>       NA          NA Climacograptus    33636
    ## 236          <NA>       NA          NA Climacograptus    33636
    ## 2530         <NA>       NA          NA Climacograptus    33636
    ## 2884         <NA>       NA          NA Climacograptus    33636
    ## 2948         <NA>       NA          NA Climacograptus    33636
    ## 3173         <NA>       NA          NA Climacograptus    33636
    ## 3246         <NA>       NA          NA Climacograptus    33636
    ## 5115         <NA>       NA          NA Climacograptus    33636
    ## 5122         <NA>       NA          NA Climacograptus    33636
    ## 5132         <NA>       NA          NA Climacograptus    33636
    ## 5154         <NA>       NA          NA Climacograptus    33636
    ## 5204         <NA>       NA          NA Climacograptus    33636
    ## 5344         <NA>       NA          NA Climacograptus    33636
    ## 5355         <NA>       NA          NA Climacograptus    33636
    ## 5365         <NA>       NA          NA Climacograptus    33636
    ## 5385         <NA>       NA          NA Climacograptus    33636
    ## 5871         <NA>       NA          NA Climacograptus    33636
    ## 5896         <NA>       NA          NA Climacograptus    33636
    ##              family family_no        order order_no         class class_no
    ## 233  Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 236  Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 2530 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 2884 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 2948 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 3173 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 3246 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5115 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5122 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5132 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5154 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5204 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5344 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5355 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5365 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5385 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5871 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5896 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ##            phylum phylum_no    authorizer     enterer   modifier
    ## 233  Hemichordata     33518     Alroy, J. Sommers, M.    unknown
    ## 236  Hemichordata     33518     Alroy, J. Sommers, M.    unknown
    ## 2530 Hemichordata     33518   Holland, S.  Hanson, T.    unknown
    ## 2884 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 2948 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 3173 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 3246 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 5115 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5122 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5132 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5154 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5204 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5344 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5355 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5365 Hemichordata     33518 Kiessling, W.  Krause, M. Krause, M.
    ## 5385 Hemichordata     33518 Kiessling, W.  Krause, M. Krause, M.
    ## 5871 Hemichordata     33518    Kroger, B.  Kroger, B.    unknown
    ## 5896 Hemichordata     33518    Wagner, P.  Wagner, P.    unknown

    ### get formal genera
    occGenus<-taxonSortPBDBocc(graptOccPBDB, rank="genus")

    occFamily<-taxonSortPBDBocc(graptOccPBDB, rank="family")
    #plot it!
    plotOccData(occSpecies,groupLabel = "Species")

![](classwork-Thurs-3-9_files/figure-markdown_strict/unnamed-chunk-1-1.png)

    ### convert occurence data to timelist format
    graptTimeSpecies<-occData2timeList(occList=occSpecies)

    ### plot diversity through time
    taxicDivDisc(graptTimeSpecies)

    head(graptTimeSpecies)

    ## $intTimes
    ##       startTime endTime
    ##  [1,]     488.3   477.7
    ##  [2,]     485.4   477.7
    ##  [3,]     485.4   471.8
    ##  [4,]     478.6   466.0
    ##  [5,]     472.0   468.9
    ##  [6,]     471.8   460.9
    ##  [7,]     471.8   458.4
    ##  [8,]     468.9   466.0
    ##  [9,]     467.3   458.4
    ## [10,]     460.9   456.1
    ## [11,]     460.9   449.5
    ## [12,]     458.4   453.0
    ## [13,]     458.4   443.4
    ## [14,]     457.5   452.0
    ## [15,]     456.1   443.4
    ## [16,]     455.8   445.6
    ## [17,]     453.0   445.6
    ## [18,]     453.0   445.2
    ## [19,]     449.5   443.7
    ## [20,]     445.2   443.4
    ## [21,]     443.4   440.8
    ## [22,]     443.4   433.4
    ## [23,]     440.8   433.4
    ## 
    ## $taxonTimes
    ##                              firstInt lastInt
    ## Adelograptus antiquus               1       3
    ## Adelograptus clarki                 2       2
    ## Amplexograptus rugosus             14      14
    ## Azygograptus novozealandicus        9      10
    ## Climacograptus bicornis            10      15
    ## Climacograptus scalaris            19      23
    ## Corynoides incurvus                14      14
    ## Corynoides tricornis               10      11
    ## Cryptograptus schaferi              7      11
    ## Cryptograptus tricornis             6      13
    ## Dicellograptus anceps              16      19
    ## Dicellograptus complanatus         17      19
    ## Dicellograptus ornatus             18      20
    ## Dicranograptus ramosus             12      12
    ## Dictyonema pulchellum               2       2
    ## Didymograptus nicholsoni            4       9
    ## Diplograptus hughesi               21      23
    ## Geniculograptus pygmaeus           11      19
    ## Goniograptus macer                  5       8
    ## Goniograptus speciosus              8       8
    ## Metabolograptus persculptus        19      21
    ## Normalograptus normalis            19      22
    ## Parabrograptus tribrachiatus       11      11
    ## Pleurograptus linearis             19      19
    ## Pleurograptus lui                  18      19
    ## Pterograptus elegans                9       9
    ## Rhaphidograptus toernquisti        21      23
    ## Tetragraptus insuetus               9       9

    taxicDivDisc(graptTimeSpecies)

![](classwork-Thurs-3-9_files/figure-markdown_strict/unnamed-chunk-1-2.png)

    head(occSpecies)

    ## $`Adelograptus antiquus`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 3609        596430  occurrence      NA       NA         63189
    ## 3612        596434  occurrence      NA       NA         63190
    ## 3627        596451  occurrence      NA       NA         63192
    ## 3630        596454  occurrence      NA       NA         63194
    ## 3632        596458  occurrence      NA       NA         63195
    ## 3667        596498  occurrence      NA       NA         63204
    ## 4223        826761  occurrence      NA       NA         91172
    ##              identified_name identified_rank identified_no
    ## 3609 Adelograptus ? antiquus         species         84007
    ## 3612 Adelograptus ? antiquus         species         84007
    ## 3627 Adelograptus ? antiquus         species         84007
    ## 3630 Adelograptus ? antiquus         species         84007
    ## 3632 Adelograptus ? antiquus         species         84007
    ## 3667 Adelograptus ? antiquus         species         84007
    ## 4223   Adelograptus antiquus         species         84007
    ##      taxonomic_reason         accepted_name accepted_rank accepted_no
    ## 3609             <NA> Adelograptus antiquus       species       84007
    ## 3612             <NA> Adelograptus antiquus       species       84007
    ## 3627             <NA> Adelograptus antiquus       species       84007
    ## 3630             <NA> Adelograptus antiquus       species       84007
    ## 3632             <NA> Adelograptus antiquus       species       84007
    ## 3667             <NA> Adelograptus antiquus       species       84007
    ## 4223             <NA> Adelograptus antiquus       species       84007
    ##      early_interval late_interval early_age late_age reference_no
    ## 3609    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 3612  Lancefieldian   Bendigonian     485.4    473.9        18179
    ## 3627  Lancefieldian   Bendigonian     485.4    473.9        18179
    ## 3630    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 3632    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 3667    Tremadocian   Tremadocian     485.4    477.7        18179
    ## 4223        Ibexian       Ibexian     488.3    471.8        24434
    ##      primary_name primary_reso subgenus_name subgenus_reso species_name
    ## 3609 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3612 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3627 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3630 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3632 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 3667 Adelograptus            ?          <NA>          <NA>     antiquus
    ## 4223 Adelograptus         <NA>          <NA>          <NA>     antiquus
    ##      species_reso subgenus subgenus_no        genus genus_no family
    ## 3609         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3612         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3627         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3630         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3632         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 3667         <NA>       NA          NA Adelograptus    33537   <NA>
    ## 4223         <NA>       NA          NA Adelograptus    33537   <NA>
    ##      family_no      order order_no         class class_no       phylum
    ## 3609        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3612        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3627        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3630        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3632        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 3667        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ## 4223        NA Dendroidea    33535 Graptolithina    33534 Hemichordata
    ##      phylum_no  authorizer     enterer  modifier
    ## 3609     33518   Hendy, A.   Hendy, A. Hendy, A.
    ## 3612     33518   Hendy, A.   Hendy, A.   unknown
    ## 3627     33518   Hendy, A.   Hendy, A.   unknown
    ## 3630     33518   Hendy, A.   Hendy, A. Hendy, A.
    ## 3632     33518   Hendy, A.   Hendy, A.   unknown
    ## 3667     33518   Hendy, A.   Hendy, A.   unknown
    ## 4223     33518 Villier, L. Villier, L.   unknown
    ## 
    ## $`Adelograptus clarki`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 3610        596431  occurrence      NA       NA         63189
    ## 3633        596459  occurrence      NA       NA         63195
    ##          identified_name identified_rank identified_no taxonomic_reason
    ## 3610 Adelograptus clarki         species         84009             <NA>
    ## 3633 Adelograptus clarki         species         84009             <NA>
    ##            accepted_name accepted_rank accepted_no early_interval
    ## 3610 Adelograptus clarki       species       84009    Tremadocian
    ## 3633 Adelograptus clarki       species       84009    Tremadocian
    ##      late_interval early_age late_age reference_no primary_name
    ## 3610   Tremadocian     485.4    477.7        18179 Adelograptus
    ## 3633   Tremadocian     485.4    477.7        18179 Adelograptus
    ##      primary_reso subgenus_name subgenus_reso species_name species_reso
    ## 3610         <NA>          <NA>          <NA>       clarki         <NA>
    ## 3633         <NA>          <NA>          <NA>       clarki         <NA>
    ##      subgenus subgenus_no        genus genus_no family family_no
    ## 3610       NA          NA Adelograptus    33537   <NA>        NA
    ## 3633       NA          NA Adelograptus    33537   <NA>        NA
    ##           order order_no         class class_no       phylum phylum_no
    ## 3610 Dendroidea    33535 Graptolithina    33534 Hemichordata     33518
    ## 3633 Dendroidea    33535 Graptolithina    33534 Hemichordata     33518
    ##      authorizer   enterer  modifier
    ## 3610  Hendy, A. Hendy, A. Hendy, A.
    ## 3633  Hendy, A. Hendy, A.   unknown
    ## 
    ## $`Amplexograptus rugosus`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 5893       1256955  occurrence      NA       NA        166800
    ##             identified_name identified_rank identified_no taxonomic_reason
    ## 5893 Amplexograptus rugosus         species        315895             <NA>
    ##               accepted_name accepted_rank accepted_no early_interval
    ## 5893 Amplexograptus rugosus       species      315895    Longvillian
    ##      late_interval early_age late_age reference_no   primary_name
    ## 5893 Marshbrookian     457.5      452          102 Amplexograptus
    ##      primary_reso subgenus_name subgenus_reso species_name species_reso
    ## 5893         <NA>          <NA>          <NA>      rugosus         <NA>
    ##      subgenus subgenus_no          genus genus_no family family_no
    ## 5893       NA          NA Amplexograptus    33615   <NA>        NA
    ##             order order_no         class class_no       phylum phylum_no
    ## 5893 Graptoloidea    33606 Graptolithina    33534 Hemichordata     33518
    ##      authorizer    enterer modifier
    ## 5893 Wagner, P. Wagner, P.  unknown
    ## 
    ## $`Azygograptus novozealandicus`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 3898        601800  occurrence      NA       NA         63967
    ## 3960        601885  occurrence      NA       NA         63960
    ## 3964        601889  occurrence      NA       NA         63961
    ## 3993        601921  occurrence      NA       NA         63963
    ## 4014        601945  occurrence      NA       NA         63965
    ##                          identified_name identified_rank identified_no
    ## 3898        Azygograptus novozealandicus         species         84630
    ## 3960        Azygograptus novozealandicus         species         84630
    ## 3964        Azygograptus novozealandicus         species         84630
    ## 3993 Azygograptus novozealandicus n. sp.         species         84630
    ## 4014        Azygograptus novozealandicus         species         84630
    ##      taxonomic_reason                accepted_name accepted_rank
    ## 3898             <NA> Azygograptus novozealandicus       species
    ## 3960             <NA> Azygograptus novozealandicus       species
    ## 3964             <NA> Azygograptus novozealandicus       species
    ## 3993             <NA> Azygograptus novozealandicus       species
    ## 4014             <NA> Azygograptus novozealandicus       species
    ##      accepted_no early_interval late_interval early_age late_age
    ## 3898       84630     Gisbornian    Gisbornian     460.9    456.1
    ## 3960       84630     Gisbornian    Gisbornian     460.9    456.1
    ## 3964       84630     Gisbornian    Gisbornian     460.9    456.1
    ## 3993       84630    Darriwilian   Darriwilian     467.3    458.4
    ## 4014       84630     Gisbornian    Gisbornian     460.9    456.1
    ##      reference_no primary_name primary_reso subgenus_name subgenus_reso
    ## 3898        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 3960        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 3964        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 3993        18428 Azygograptus         <NA>          <NA>          <NA>
    ## 4014        18428 Azygograptus         <NA>          <NA>          <NA>
    ##         species_name species_reso subgenus subgenus_no        genus
    ## 3898 novozealandicus         <NA>       NA          NA Azygograptus
    ## 3960 novozealandicus         <NA>       NA          NA Azygograptus
    ## 3964 novozealandicus         <NA>       NA          NA Azygograptus
    ## 3993 novozealandicus       n. sp.       NA          NA Azygograptus
    ## 4014 novozealandicus         <NA>       NA          NA Azygograptus
    ##      genus_no family family_no        order order_no         class
    ## 3898    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 3960    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 3964    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 3993    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ## 4014    33628   <NA>        NA Graptoloidea    33606 Graptolithina
    ##      class_no       phylum phylum_no authorizer   enterer modifier
    ## 3898    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 3960    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 3964    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 3993    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 4014    33534 Hemichordata     33518  Hendy, A. Hendy, A.  unknown
    ## 
    ## $`Climacograptus bicornis`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 2399        246238  occurrence      NA       NA         24117
    ## 4166        748935  occurrence      NA       NA         80104
    ## 4320        955088  occurrence      NA       NA        111711
    ## 4325        955095  occurrence      NA       NA        111713
    ## 4332        955103  occurrence      NA       NA        111718
    ## 4516        996584  occurrence      NA       NA        120528
    ## 4685       1139721  occurrence      NA       NA        145233
    ## 4695       1139731  occurrence      NA       NA        145236
    ## 4703       1139741  occurrence      NA       NA        145237
    ## 4713       1139751  occurrence      NA       NA        145238
    ## 4725       1139763  occurrence      NA       NA        145240
    ## 4773       1141828  occurrence      NA       NA        145463
    ## 4774       1141829  occurrence      NA       NA        145464
    ## 5330       1144012  occurrence      NA       NA        145615
    ##              identified_name identified_rank identified_no
    ## 2399 Climacograptus bicornis         species        306375
    ## 4166 Climacograptus bicornis         species        306375
    ## 4320 Climacograptus bicornis         species        306375
    ## 4325 Climacograptus bicornis         species        306375
    ## 4332 Climacograptus bicornis         species        306375
    ## 4516 Climacograptus bicornis         species        306375
    ## 4685 Climacograptus bicornis         species        306375
    ## 4695 Climacograptus bicornis         species        306375
    ## 4703 Climacograptus bicornis         species        306375
    ## 4713 Climacograptus bicornis         species        306375
    ## 4725 Climacograptus bicornis         species        306375
    ## 4773 Climacograptus bicornis         species        306375
    ## 4774 Climacograptus bicornis         species        306375
    ## 5330 Climacograptus bicornis         species        306375
    ##      taxonomic_reason           accepted_name accepted_rank accepted_no
    ## 2399             <NA> Climacograptus bicornis       species      306375
    ## 4166             <NA> Climacograptus bicornis       species      306375
    ## 4320             <NA> Climacograptus bicornis       species      306375
    ## 4325             <NA> Climacograptus bicornis       species      306375
    ## 4332             <NA> Climacograptus bicornis       species      306375
    ## 4516             <NA> Climacograptus bicornis       species      306375
    ## 4685             <NA> Climacograptus bicornis       species      306375
    ## 4695             <NA> Climacograptus bicornis       species      306375
    ## 4703             <NA> Climacograptus bicornis       species      306375
    ## 4713             <NA> Climacograptus bicornis       species      306375
    ## 4725             <NA> Climacograptus bicornis       species      306375
    ## 4773             <NA> Climacograptus bicornis       species      306375
    ## 4774             <NA> Climacograptus bicornis       species      306375
    ## 5330             <NA> Climacograptus bicornis       species      306375
    ##       early_interval   late_interval early_age late_age reference_no
    ## 2399      Trentonian     Richmondian     460.9    443.7         6817
    ## 4166         Idavere         Idavere     460.9    455.8        26936
    ## 4320 Late Ordovician Late Ordovician     458.4    443.4        36540
    ## 4325 Late Ordovician Late Ordovician     458.4    443.4        36540
    ## 4332 Late Ordovician Late Ordovician     458.4    443.4        36540
    ## 4516        Sandbian        Sandbian     458.4    453.0        38521
    ## 4685      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4695      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4703      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4713      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4725      Gisbornian      Gisbornian     460.9    456.1        46966
    ## 4773       Eastonian       Eastonian     456.1    449.5        46966
    ## 4774       Eastonian       Eastonian     456.1    449.5        46966
    ## 5330      Caradocian      Caradocian     460.9    449.5        47089
    ##        primary_name primary_reso subgenus_name subgenus_reso species_name
    ## 2399 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4166 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4320 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4325 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4332 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4516 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4685 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4695 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4703 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4713 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4725 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4773 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 4774 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ## 5330 Climacograptus         <NA>          <NA>          <NA>     bicornis
    ##      species_reso subgenus subgenus_no          genus genus_no
    ## 2399         <NA>       NA          NA Climacograptus    33636
    ## 4166         <NA>       NA          NA Climacograptus    33636
    ## 4320         <NA>       NA          NA Climacograptus    33636
    ## 4325         <NA>       NA          NA Climacograptus    33636
    ## 4332         <NA>       NA          NA Climacograptus    33636
    ## 4516         <NA>       NA          NA Climacograptus    33636
    ## 4685         <NA>       NA          NA Climacograptus    33636
    ## 4695         <NA>       NA          NA Climacograptus    33636
    ## 4703         <NA>       NA          NA Climacograptus    33636
    ## 4713         <NA>       NA          NA Climacograptus    33636
    ## 4725         <NA>       NA          NA Climacograptus    33636
    ## 4773         <NA>       NA          NA Climacograptus    33636
    ## 4774         <NA>       NA          NA Climacograptus    33636
    ## 5330         <NA>       NA          NA Climacograptus    33636
    ##              family family_no        order order_no         class class_no
    ## 2399 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4166 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4320 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4325 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4332 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4516 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4685 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4695 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4703 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4713 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4725 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4773 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 4774 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5330 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ##            phylum phylum_no           authorizer    enterer   modifier
    ## 2399 Hemichordata     33518          Holland, S. Hanson, T.    unknown
    ## 4166 Hemichordata     33518 Novack-Gottshall, P.  Hearn, P. Wagner, P.
    ## 4320 Hemichordata     33518           Miller, A.  Kolbe, S.  Kolbe, S.
    ## 4325 Hemichordata     33518           Miller, A.  Kolbe, S.    unknown
    ## 4332 Hemichordata     33518           Miller, A.  Kolbe, S.    unknown
    ## 4516 Hemichordata     33518        Kiessling, W. Merkel, U.    unknown
    ## 4685 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4695 Hemichordata     33518        Kiessling, W. Krause, M. Krause, M.
    ## 4703 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4713 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4725 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 4773 Hemichordata     33518        Kiessling, W. Krause, M. Krause, M.
    ## 4774 Hemichordata     33518        Kiessling, W. Krause, M. Krause, M.
    ## 5330 Hemichordata     33518        Kiessling, W. Krause, M.    unknown
    ## 
    ## $`Climacograptus scalaris`
    ##      occurrence_no record_type reid_no obsolete collection_no
    ## 233          41894  occurrence      NA       NA          3281
    ## 236          41899  occurrence      NA       NA          3282
    ## 2530        260374  occurrence      NA       NA         25168
    ## 2884        285928  occurrence      NA       NA         27197
    ## 2948        287240  occurrence      NA       NA         27388
    ## 3173        291182  occurrence      NA       NA         27782
    ## 3246        292390  occurrence      NA       NA         27838
    ## 5115       1143763  occurrence      NA       NA        145587
    ## 5122       1143780  occurrence      NA       NA        145589
    ## 5132       1143790  occurrence      NA       NA        145590
    ## 5154       1143812  occurrence      NA       NA        145591
    ## 5204       1143865  occurrence      NA       NA        145598
    ## 5344       1144116  occurrence      NA       NA        145653
    ## 5355       1144128  occurrence      NA       NA        145654
    ## 5365       1144142  occurrence      NA       NA        145655
    ## 5385       1144162  occurrence      NA       NA        145656
    ## 5871       1218886  occurrence      NA       NA        159343
    ## 5896       1257991  occurrence      NA       NA        166909
    ##                identified_name identified_rank identified_no
    ## 233    Climacograptus scalaris         species        316364
    ## 236    Climacograptus scalaris         species        316364
    ## 2530   Climacograptus scalaris         species        316364
    ## 2884   Climacograptus scalaris         species        316364
    ## 2948   Climacograptus scalaris         species        316364
    ## 3173   Climacograptus scalaris         species        316364
    ## 3246   Climacograptus scalaris         species        316364
    ## 5115   Climacograptus scalaris         species        316364
    ## 5122 Climacograptus ? scalaris         species        316364
    ## 5132   Climacograptus scalaris         species        316364
    ## 5154   Climacograptus scalaris         species        316364
    ## 5204   Climacograptus scalaris         species        316364
    ## 5344   Climacograptus scalaris         species        316364
    ## 5355   Climacograptus scalaris         species        316364
    ## 5365   Climacograptus scalaris         species        316364
    ## 5385   Climacograptus scalaris         species        316364
    ## 5871   Climacograptus scalaris         species        316364
    ## 5896   Climacograptus scalaris         species        316364
    ##      taxonomic_reason           accepted_name accepted_rank accepted_no
    ## 233              <NA> Climacograptus scalaris       species      316364
    ## 236              <NA> Climacograptus scalaris       species      316364
    ## 2530             <NA> Climacograptus scalaris       species      316364
    ## 2884             <NA> Climacograptus scalaris       species      316364
    ## 2948             <NA> Climacograptus scalaris       species      316364
    ## 3173             <NA> Climacograptus scalaris       species      316364
    ## 3246             <NA> Climacograptus scalaris       species      316364
    ## 5115             <NA> Climacograptus scalaris       species      316364
    ## 5122             <NA> Climacograptus scalaris       species      316364
    ## 5132             <NA> Climacograptus scalaris       species      316364
    ## 5154             <NA> Climacograptus scalaris       species      316364
    ## 5204             <NA> Climacograptus scalaris       species      316364
    ## 5344             <NA> Climacograptus scalaris       species      316364
    ## 5355             <NA> Climacograptus scalaris       species      316364
    ## 5365             <NA> Climacograptus scalaris       species      316364
    ## 5385             <NA> Climacograptus scalaris       species      316364
    ## 5871             <NA> Climacograptus scalaris       species      316364
    ## 5896             <NA> Climacograptus scalaris       species      316364
    ##      early_interval late_interval early_age late_age reference_no
    ## 233        Aeronian      Aeronian     440.8    438.5          155
    ## 236        Aeronian      Aeronian     440.8    438.5          155
    ## 2530    Alexandrian   Alexandrian     443.4    436.0         7063
    ## 2884     Llandovery    Llandovery     443.4    433.4         7455
    ## 2948     Rhuddanian    Rhuddanian     443.4    440.8         7455
    ## 3173     Llandovery    Llandovery     443.4    433.4         7624
    ## 3246     Llandovery    Llandovery     443.4    433.4         7624
    ## 5115     Llandovery    Llandovery     443.4    433.4        47076
    ## 5122     Llandovery    Llandovery     443.4    433.4        47076
    ## 5132     Llandovery    Llandovery     443.4    433.4        47076
    ## 5154     Llandovery    Llandovery     443.4    433.4        47076
    ## 5204     Llandovery    Llandovery     443.4    433.4        47083
    ## 5344     Rhuddanian    Rhuddanian     443.4    440.8        47103
    ## 5355     Rhuddanian    Rhuddanian     443.4    440.8        47103
    ## 5365       Aeronian      Aeronian     440.8    438.5        47103
    ## 5385       Aeronian      Aeronian     440.8    438.5        47103
    ## 5871       Aeronian      Aeronian     440.8    438.5        52096
    ## 5896      Bolindian     Bolindian     449.5    443.7           78
    ##        primary_name primary_reso subgenus_name subgenus_reso species_name
    ## 233  Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 236  Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 2530 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 2884 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 2948 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 3173 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 3246 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5115 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5122 Climacograptus            ?          <NA>          <NA>     scalaris
    ## 5132 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5154 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5204 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5344 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5355 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5365 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5385 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5871 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ## 5896 Climacograptus         <NA>          <NA>          <NA>     scalaris
    ##      species_reso subgenus subgenus_no          genus genus_no
    ## 233          <NA>       NA          NA Climacograptus    33636
    ## 236          <NA>       NA          NA Climacograptus    33636
    ## 2530         <NA>       NA          NA Climacograptus    33636
    ## 2884         <NA>       NA          NA Climacograptus    33636
    ## 2948         <NA>       NA          NA Climacograptus    33636
    ## 3173         <NA>       NA          NA Climacograptus    33636
    ## 3246         <NA>       NA          NA Climacograptus    33636
    ## 5115         <NA>       NA          NA Climacograptus    33636
    ## 5122         <NA>       NA          NA Climacograptus    33636
    ## 5132         <NA>       NA          NA Climacograptus    33636
    ## 5154         <NA>       NA          NA Climacograptus    33636
    ## 5204         <NA>       NA          NA Climacograptus    33636
    ## 5344         <NA>       NA          NA Climacograptus    33636
    ## 5355         <NA>       NA          NA Climacograptus    33636
    ## 5365         <NA>       NA          NA Climacograptus    33636
    ## 5385         <NA>       NA          NA Climacograptus    33636
    ## 5871         <NA>       NA          NA Climacograptus    33636
    ## 5896         <NA>       NA          NA Climacograptus    33636
    ##              family family_no        order order_no         class class_no
    ## 233  Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 236  Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 2530 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 2884 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 2948 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 3173 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 3246 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5115 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5122 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5132 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5154 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5204 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5344 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5355 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5365 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5385 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5871 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ## 5896 Diplograptidae    150197 Graptoloidea    33606 Graptolithina    33534
    ##            phylum phylum_no    authorizer     enterer   modifier
    ## 233  Hemichordata     33518     Alroy, J. Sommers, M.    unknown
    ## 236  Hemichordata     33518     Alroy, J. Sommers, M.    unknown
    ## 2530 Hemichordata     33518   Holland, S.  Hanson, T.    unknown
    ## 2884 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 2948 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 3173 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 3246 Hemichordata     33518     Foote, M.   Foote, M.    unknown
    ## 5115 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5122 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5132 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5154 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5204 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5344 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5355 Hemichordata     33518 Kiessling, W.  Krause, M.    unknown
    ## 5365 Hemichordata     33518 Kiessling, W.  Krause, M. Krause, M.
    ## 5385 Hemichordata     33518 Kiessling, W.  Krause, M. Krause, M.
    ## 5871 Hemichordata     33518    Kroger, B.  Kroger, B.    unknown
    ## 5896 Hemichordata     33518    Wagner, P.  Wagner, P.    unknown

    plotOccData(occSpecies,groupLabel = "Species")

![](classwork-Thurs-3-9_files/figure-markdown_strict/unnamed-chunk-2-1.png)

    plotOccData(occGenus, groupLabel = "Genera")

![](classwork-Thurs-3-9_files/figure-markdown_strict/unnamed-chunk-2-2.png)

    plotOccData(occGenus, groupLabel = "Families")

![](classwork-Thurs-3-9_files/figure-markdown_strict/unnamed-chunk-2-3.png)

    pdf(file= "ranges.pdf")
    plotOccData(occSpecies,groupLabel = "Species")
    plotOccData(occGenus, groupLabel = "Genera")
    plotOccData(occGenus, groupLabel = "Families")
    dev.off()

    ## png 
    ##   2

    graptTimeSpecies<-occData2timeList(occList=occSpecies)
    graptTimeGenus<-occData2timeList(occList=occGenus)
    graptTimeFamily<-occData2timeList(occList=occFamily)
    layout(1:3)
    taxicDivDisc(graptTimeSpecies)
    taxicDivDisc(graptTimeGenus)
    taxicDivDisc(graptTimeFamily)

![](classwork-Thurs-3-9_files/figure-markdown_strict/unnamed-chunk-2-4.png)

    dev.off()

    ## null device 
    ##           1

    pdf(file="dtt.pdf")
    taxicDivDisc(graptTimeSpecies)
    taxicDivDisc(graptTimeGenus)
    taxicDivDisc(graptTimeFamily)
    dev.off()

    ## null device 
    ##           1

Using the canid data set

    library(paleobioDB)
    #canids <-pbdb_occurrences (limit="all", vocab= "pbdb", base_name="Canidae", show=c('phylo', 'ident'))
    #head(canids)
