<style>
    .main {
        border: 0;
        border-bottom: 2px solid #1976D2;
        width: 100%;
        font-size: 30px;
        line-height: 35px;
        height: 70px;
        text-align: center;
        padding: 10px;
        background: transparent;
        color: #BBDEFB;
    }

    ul {
        margin: 0 auto;
        padding: 0;
        max-height: 390px;
        overflow-y: auto;
        border: 1px solid rgba(0, 0, 0, 0.1);
        padding: 5px 5px 0 5px;
        border-left: none;
        border-right: none;
    }

    li {
        list-style: none;
        background-color: rgba(0, 0, 0, 0.05);
        background-image: linear-gradient( 90deg,
        #FFD32E 10px,
        #EEE 10px,
        #EEE 11px,
        transparent 11px);
        padding: 10px 15px 10px 25px;
        border: 1px solid #CCC;
        box-shadow: inset 1px 1px 0 rgba(255, 255, 255, 0.5);
        margin-bottom: 5px;
        width: 100%;
        box-sizing: border-box;
        cursor: pointer;
        border-radius: 3px;
    }
</style>
<input id='main' class='main' placeholder="XAW100006..." maxlength="9">
<ul id="valid">
</ul>

<script>
    let fs = {
        '1.0.0': [
            ['XAW100006', 'XAW100128'],
            ['XAW700015', 'XAW700030'],
            ['XAJ100022', 'XAJ100042'],
            ['XAJ400020', 'XAJ400081'],
            ['XAJ700012', 'XAJ700065'],
        ],
        '2.1.0': [
            ['XAW100139', 'XAW100140'],
            ['XAW700049', 'XAW700050'],
            ['?', 'XAJ400126'],
            ['XAJ700078', 'XAJ700085']
        ],
        '2.2.0': [
            ['XAW100158', 'XAW100173'],
            ['XAJ400107', 'XAJ400174'],
            ['XAJ700091', 'XAJ700093'],
        ],
        '2.3.0': [
            ['XAW100179', 'XAW100210'],
            ['XAW400012', 'XAW400016'],
            ['?', 'XAW700050'],
            ['?', 'XAJ100086'],
            ['XAJ400105', 'XAJ400154'],
            ['XAJ700098', 'XAJ700132'],
        ],
        '3.0.0': [
            ['XAW100182', 'XAW100228'],
            ['XAW400017', 'XAW400033'],
            ['XAW700059', 'XAW700079'],
            ['XAJ100117', 'XAJ100129'],
            ['XAJ400169', 'XAJ400187'],
            ['XAJ700135', 'XAJ700138'],
        ],
        '3.0.1': [
            ['XAW100238', 'XAW100282'],
            ['?', 'XAW400028'],
            ['?', 'XAJ100122'],
            ['XAJ400210', 'XAJ400241'],
            ['XAJ700150', 'XAJ700163'],
        ],
        '3.0.2': [
            ['XAW100350', 'XAW100409'],
        ],
    }
    let input = document.getElementById('main');
    let list = document.getElementById('valid');
    let MAX = 9;
    input.addEventListener('input', function () {
        let s = input.value.toUpperCase();
        let sLen = s.length;
        s = s + '0'.repeat(MAX - sLen);
        console.log(s);
        let res = [];
        for (let firm of Object.keys(fs)) {
            let serials = fs[firm];
            for (let serial of serials) {
                let [min, max] = serial;
                if (s >= min && s <= max) {
                    res.push(`${firm} = ${min} - ${max}`);
                }
            }
        }
        let list = '<li>' + res.join('</li><li>') + '</li>';
        document.getElementById('valid').innerHTML = list;
    });



</script>