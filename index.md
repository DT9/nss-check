<input id='main'>

<script>
    var fs = {
        '1.0.0': [
            ['XAW100006','XAW100128'],
            ['XAW700015','XAW700030'],
            ['XAJ100022','XAJ100042'],
            ['XAJ400020','XAJ400081'],
            ['XAJ700012','XAJ700065'],
        ],
        '2.1.0': [
            ['XAW100139','XAW100140'],
            ['XAW700049','XAW700050'],
            ['?','XAJ400126'],
            ['XAJ700078','XAJ700085']
        ],
        '2.2.0':[
            ['XAW100158','XAW100173'],
            ['XAJ400107','XAJ400174'],
            ['XAJ700091','XAJ700093'],
        ],
        '2.3.0':[
            ['XAW100179','XAW100210'],
            ['XAW400012','XAW400016'],
            ['?','XAW700050'],
            ['?','XAJ100086'],
            ['XAJ400105','XAJ400154'],
            ['XAJ700098','XAJ700132'],
        ],
        '3.0.0':[
            ['XAW100182','XAW100228'],
            ['XAW400017','XAW400033'],
            ['XAW700059','XAW700079'],
            ['XAJ100117','XAJ100129'],
            ['XAJ400169','XAJ400187'],
            ['XAJ700135','XAJ700138'],
        ],
        '3.0.1':[
            ['XAW100238','XAW100282'],
            ['?','XAW400028'],
            ['?','XAJ100122'],
            ['XAJ400210','XAJ400241'],
            ['XAJ700150','XAJ700163'],
        ],
        '3.0.2':[
            ['XAW100350','XAW100409'],
        ],
    }
    var input = document.getElementById('main');

    input.addEventListener('input', function () {
        var s = input.value;
        var sLen = input.value.length;
        var res = [];
        for (let firm of Object.keys(fs)) {
            serials = fs[firm];
            for (let serial of serials) {
                min,max = serial;
                if (min <= s <= max) {
                    res.push(serial);
                }
            }
        }
        console.log(res);

    });



</script>