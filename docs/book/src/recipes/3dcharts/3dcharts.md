# Scatter 3D Charts

The following imports have been used to produce the plots below:

```rust
use itertools_num::linspace;
use plotly::common::{
    ColorScale, ColorScalePalette, DashType, Fill, Font, Line, LineShape, Marker, Mode, Title,
};
use plotly::layout::{Axis, BarMode, Layout, Legend, TicksDirection};
use plotly::Sankey;
use rand_distr::{Distribution, Normal, Uniform};
```

The `to_inline_html` method is used to produce the html plot displayed in this page.

## Constructing a basic Scatter 3D plot
```rust
let n: usize = 100;
let t: Vec<f64> = linspace(0., 10., n).collect();
let y: Vec<f64> = t.iter().map(|x| x.sin()).collect();
let z: Vec<f64> = t.iter().map(|x| x.cos()).collect();

let trace = Scatter3D::new(t, y, z).mode(Mode::Markers);
let mut plot = Plot::new();
plot.add_trace(trace);
```
<div id="basic-scatter3d" class="plotly-graph-div" style="height:100%; width:100%;"></div>
<script type="text/javascript">
    window.PLOTLYENV=window.PLOTLYENV || {};
    if (document.getElementById("basic-scatter3d")) {
        Plotly.newPlot('basic-scatter3d', {
  "data": [
    {
      "type": "scatter3d",
      "mode": "markers",
      "x": [
        0.0,
        0.10101010101010101,
        0.20202020202020202,
        0.30303030303030304,
        0.40404040404040403,
        0.5050505050505051,
        0.6060606060606061,
        0.7070707070707071,
        0.8080808080808081,
        0.9090909090909091,
        1.0101010101010102,
        1.1111111111111112,
        1.2121212121212122,
        1.3131313131313131,
        1.4141414141414141,
        1.5151515151515151,
        1.6161616161616161,
        1.7171717171717171,
        1.8181818181818181,
        1.9191919191919191,
        2.0202020202020203,
        2.121212121212121,
        2.2222222222222223,
        2.323232323232323,
        2.4242424242424243,
        2.525252525252525,
        2.6262626262626263,
        2.727272727272727,
        2.8282828282828283,
        2.929292929292929,
        3.0303030303030303,
        3.131313131313131,
        3.2323232323232323,
        3.3333333333333335,
        3.4343434343434343,
        3.5353535353535355,
        3.6363636363636362,
        3.7373737373737375,
        3.8383838383838382,
        3.9393939393939394,
        4.040404040404041,
        4.141414141414141,
        4.242424242424242,
        4.343434343434343,
        4.444444444444445,
        4.545454545454545,
        4.646464646464646,
        4.747474747474747,
        4.848484848484849,
        4.94949494949495,
        5.05050505050505,
        5.151515151515151,
        5.252525252525253,
        5.353535353535354,
        5.454545454545454,
        5.555555555555555,
        5.656565656565657,
        5.757575757575758,
        5.858585858585858,
        5.959595959595959,
        6.0606060606060606,
        6.161616161616162,
        6.262626262626262,
        6.363636363636363,
        6.4646464646464645,
        6.565656565656566,
        6.666666666666667,
        6.767676767676767,
        6.8686868686868685,
        6.96969696969697,
        7.070707070707071,
        7.171717171717171,
        7.2727272727272725,
        7.373737373737374,
        7.474747474747475,
        7.575757575757575,
        7.6767676767676765,
        7.777777777777778,
        7.878787878787879,
        7.979797979797979,
        8.080808080808081,
        8.181818181818182,
        8.282828282828282,
        8.383838383838384,
        8.484848484848484,
        8.585858585858587,
        8.686868686868687,
        8.787878787878787,
        8.88888888888889,
        8.98989898989899,
        9.09090909090909,
        9.191919191919192,
        9.292929292929292,
        9.393939393939394,
        9.494949494949495,
        9.595959595959595,
        9.696969696969697,
        9.797979797979798,
        9.8989898989899,
        10.0
      ],
      "y": [
        0.0,
        0.1008384202581046,
        0.2006488565226854,
        0.2984138044476411,
        0.3931366121483298,
        0.48385164043793466,
        0.5696341069089657,
        0.6496095135057065,
        0.7229625614794605,
        0.7889454628442574,
        0.8468855636029834,
        0.8961922010299563,
        0.9363627251042848,
        0.9669876227092996,
        0.9877546923600838,
        0.9984522269003895,
        0.9989711717233568,
        0.9893062365143401,
        0.9695559491823237,
        0.9399216514301312,
        0.9007054462029555,
        0.8523071179396752,
        0.7952200570230491,
        0.7300262299764464,
        0.6573902466827755,
        0.5780525851065732,
        0.4928220425889235,
        0.40256749066949654,
        0.30820901749007684,
        0.2107085480771929,
        0.11106003812412972,
        0.010279341240534697,
        -0.09060614703340773,
        -0.19056796287548539,
        -0.28858705872043244,
        -0.38366419180611233,
        -0.47483011082223947,
        -0.5611554368152017,
        -0.6417601376193878,
        -0.7158224992291902,
        -0.7825875026542022,
        -0.8413745208608701,
        -0.8915842573351402,
        -0.9327048555318336,
        -0.9643171169287782,
        -0.9860987744909296,
        -0.9978277779792126,
        -0.9993845576124357,
        -0.9907532430056771,
        -0.9720218249588334,
        -0.9433812584459996,
        -0.9051235159501367,
        -0.8576386109880517,
        -0.8014106221689697,
        -0.7370127583189133,
        -0.6651015149788224,
        -0.586409981847235,
        -0.5017403693939113,
        -0.4119558308308628,
        -0.31797166281061867,
        -0.22074597455506334,
        -0.12126992053716677,
        -0.020557596287260064,
        0.08036429967028173,
        0.18046693235991093,
        0.27872981867755725,
        0.37415123057121996,
        0.4657584070256517,
        0.5526174707464059,
        0.6338429484489058,
        0.7086067976992182,
        0.7761468482835805,
        0.8357745720522589,
        0.8868821020290788,
        0.9289484292312513,
        0.9615447140268235,
        0.9843386578838236,
        0.9970978909438748,
        0.9996923408861117,
        0.9920955589323228,
        0.9743849894755358,
        0.9467411805833543,
        0.9094459434244625,
        0.8628794793817836,
        0.8075165041395626,
        0.7439214082568444,
        0.6727425035622647,
        0.5947054140244975,
        0.510605678474283,
        0.4213006405886069,
        0.32770070881349983,
        0.23076007532505177,
        0.13146698864295842,
        0.03083367906114098,
        -0.07011396040064677,
        -0.1703468323280965,
        -0.26884312591038406,
        -0.3645987336558887,
        -0.45663748763377376,
        -0.5440211108893698
      ],
      "z": [
        1.0,
        0.9949028158568303,
        0.9796632259996998,
        0.9544365884201449,
        0.9194800727522776,
        0.8751500385908233,
        0.82189840263017,
        0.7602680316591506,
        0.6908872083770674,
        0.6144632264484674,
        0.5317751800910392,
        0.4436660217022285,
        0.3510339684920502,
        0.25482334572604864,
        0.15601495992575853,
        0.05561610016580674,
        -0.04534973060188524,
        -0.1458532495141353,
        -0.24486988668507892,
        -0.3413902300489206,
        -0.43443031567828566,
        -0.5230416586748752,
        -0.6063209223738354,
        -0.6834191272904034,
        -0.7535503059294446,
        -0.815999515227557,
        -0.8701301249459654,
        -0.9153903077136358,
        -0.9513186645587279,
        -0.9775489285796396,
        -0.993813698804694,
        -0.9999471661761239,
        -0.9958868038686729,
        -0.981674004711079,
        -0.9574536592123347,
        -0.9234726784944765,
        -0.8800774771896732,
        -0.8277104419618857,
        -0.7669054216542901,
        -0.69828228503756,
        -0.6225406016393301,
        -0.5404525100747903,
        -0.45285484658127084,
        -0.3606406140014481,
        -0.2647498781834829,
        -0.16616018460355267,
        -0.06587659290724678,
        0.03507856903860484,
        0.13567612713271912,
        0.23489055281917826,
        0.33171041770321597,
        0.42514870442477243,
        0.5142528686769626,
        0.5981145497935533,
        0.6758788309121296,
        0.7467529543114478,
        0.810014403075603,
        0.865018266697566,
        0.9112038155344026,
        0.9481002170917641,
        0.9753313358637337,
        0.9926195677967009,
        0.9997886702873213,
        0.9967655588645231,
        0.983581052239521,
        0.9603695581285238,
        0.9273677030509753,
        0.8849119200716687,
        0.8334350190781794,
        0.7734617745574747,
        0.7056035758515253,
        0.6305521944291881,
        0.5490727317130796,
        0.4619958193539013,
        0.3702091514654802,
        0.2746484351440477,
        0.17628785152548898,
        0.07613012462407193,
        -0.02480370080544784,
        -0.12548466817409182,
        -0.22488639862108173,
        -0.3219955542979381,
        -0.41582216870771727,
        -0.5054097387880672,
        -0.5898449758557073,
        -0.6682671160076287,
        -0.7398766950653171,
        -0.80394369860703,
        -0.859815004003662,
        -0.9069210385913591,
        -0.9447815861050266,
        -0.973010682179788,
        -0.9913205490138658,
        -0.9995245290814802,
        -0.9975389879884077,
        -0.9853841670717991,
        -0.9631839770525324,
        -0.9311647348436916,
        -0.8896528563926016,
        -0.8390715290764524
      ]
    }
  ],
  "layout": {},
  "config": {}
});
    };
</script>