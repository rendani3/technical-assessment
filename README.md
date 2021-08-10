const data = [



{
    "id": 1,
    "model": "1 Series",
    "colour": "white",
    "manufacturer": "BMW",
    "salesHistory": [{
        "year": "2011",
        "vehiclesSold": 2991
      },
      {
        "year": "2012",
        "vehiclesSold": 3228
      },
      {
        "year": 2013,
        "vehiclesSold": 7841
      },
      {
        "year": 2014,
        "vehiclesSold": 8458
      },
      {
        "year": 2015,
        "vehiclesSold": 7963
      },
      {
        "year": 2016,
        "vehiclesSold": 5220
      },
      {
        "year": 2017,
        "vehiclesSold": 7043
      },
      {
        "year": 2018,
        "vehiclesSold": 5369
      },
      {
        "year": 2019,
        "vehiclesSold": 3564
      },
      {
        "year": 2020,
        "vehiclesSold": 3646
      }
    ]
  },
  {
    "id": 2,
    "model": "2 Series",
    "colour": "black",
    "manufacturer": "BMW",
    "salesHistory": [{
        "year": 2011,
        "vehiclesSold": 8540
      },
      {
        "year": 2012,
        "vehiclesSold": 4274
      },
      {
        "year": 2013,
        "vehiclesSold": 6995
      },
      {
        "year": 2014,
        "vehiclesSold": 1618
      },
      {
        "year": 2015,
        "vehiclesSold": 3754
      },
      {
        "year": 2016,
        "vehiclesSold": 2048
      },
      {
        "year": 2017,
        "vehiclesSold": 2715
      },
      {
        "year": 2018,
        "vehiclesSold": 3626
      },
      {
        "year": 2019,
        "vehiclesSold": 9052
      },
      {
        "year": 2020,
        "vehiclesSold": 7605
      }
    ]
  },
  {
    "id": 3,
    "model": "3 Series",
    "colour": "black",
    "manufacturer": "BMW",
    "salesHistory": [{
        "year": 2011,
        "vehiclesSold": 6260
      },
      {
        "year": 2012,
        "vehiclesSold": 9637
      },
      {
        "year": 2013,
        "vehiclesSold": 5971
      },
      {
        "year": 2014,
        "vehiclesSold": 2467
      },
      {
        "year": 2015,
        "vehiclesSold": 7512
      },
      {
        "year": 2016,
        "vehiclesSold": 9483
      },
      {
        "year": 2017,
        "vehiclesSold": 7955
      },
      {
        "year": 2018,
        "vehiclesSold": 5098
      },
      {
        "year": 2019,
        "vehiclesSold": 9860
      },
      {
        "year": 2020,
        "vehiclesSold": 9051
      }
    ]
  },
  {
    "id": 4,
    "model": "A Class",
    "colour": "white",
    "manufacturer": "Mercedes",
    "salesHistory": [{
        "year": 2011,
        "vehiclesSold": 1508
      },
      {
        "year": 2012,
        "vehiclesSold": 8137
      },
      {
        "year": 2013,
        "vehiclesSold": 5572
      },
      {
        "year": 2014,
        "vehiclesSold": 6820
      },
      {
        "year": 2015,
        "vehiclesSold": 1387
      },
      {
        "year": 2016,
        "vehiclesSold": 8517
      },
      {
        "year": 2017,
        "vehiclesSold": 6608
      },
      {
        "year": 2018,
        "vehiclesSold": 6190
      },
      {
        "year": 2019,
        "vehiclesSold": 5956
      },
      {
        "year": 2020,
        "vehiclesSold": 5847
      }
    ]
  },
  {
    "id": 5,
    "model": "B Class",
    "colour": "grey",
    "manufacturer": "Mercedes",
    "salesHistory": [{
        "year": 2011,
        "vehiclesSold": 6176
      },
      {
        "year": 2012,
        "vehiclesSold": 8463
      },
      {
        "year": 2013,
        "vehiclesSold": 7981
      },
      {
        "year": 2014,
        "vehiclesSold": 9000
      },
      {
        "year": 2015,
        "vehiclesSold": 2978
      },
      {
        "year": 2016,
        "vehiclesSold": 8366
      },
      {
        "year": 2017,
        "vehiclesSold": 2109
      },
      {
        "year": 2018,
        "vehiclesSold": 3104
      },
      {
        "year": 2019,
        "vehiclesSold": 4170
      },
      {
        "year": 2020,
        "vehiclesSold": 4851
      }
    ]
  },
  {
    "id": 6,
    "model": "Golf",
    "colour": "white",
    "manufacturer": "VW",
    "salesHistory": [{
        "year": 2011,
        "vehiclesSold": 2767
      },
      {
        "year": 2012,
        "vehiclesSold": 4174
      },
      {
        "year": 2013,
        "vehiclesSold": 4398
      },
      {
        "year": 2014,
        "vehiclesSold": 5511
      },
      {
        "year": 2015,
        "vehiclesSold": 1584
      },
      {
        "year": 2016,
        "vehiclesSold": 9484
      },
      {
        "year": 2017,
        "vehiclesSold": 7953
      },
      {
        "year": 2018,
        "vehiclesSold": 9934
      },
      {
        "year": 2019,
        "vehiclesSold": 2575
      },
      {
        "year": 2020,
        "vehiclesSold": 9300
      }
    ]
  }
];

const reduceSalesHistory = (salesHistory) => {
  return salesHistory.reduce((acc, curr) => (acc + curr.vehiclesSold), 0);
}

let manufacturs = data.reduce((acc, curr) => {
  acc[curr.manufacturer] = ((acc[curr.manufacturer] || 0) + reduceSalesHistory(curr.salesHistory));
  return acc;
}, {});

let models = data.reduce((acc, curr) => {
  acc[curr.model] = reduceSalesHistory(curr.salesHistory);
  return acc;
}, {});

let totalSold = data.reduce((acc, curr) => {
  acc += reduceSalesHistory(curr.salesHistory);
  return acc;
}, 0);

let coloursTotal = data.reduce((acc, curr) => {
  acc[curr.colour] = ((acc[curr.colour] || 0) + reduceSalesHistory(curr.salesHistory));
  return acc;
}, {});

let mostPopColor = Object.keys(coloursTotal).reduce((a, b) => coloursTotal[a] > coloursTotal[b] ? a : b);

console.log(models);
console.log(manufacturs);
console.log(totalSold);
console.log(mostPopColor)
