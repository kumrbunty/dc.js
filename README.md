# dc.js

var hubChart = dc.barChart("#hub-chart");

var dateHub = dateCF.dimension(function(d){ return d.hub;}),
    dateHubs = dateHub.group().reduceSum(function(d){
        return d.total;
    });

var minHub = dateHub.bottom(1)[0].hub;
var maxHub = dateHub.top(1)[0].hub;

hubChart.width(0.40 * window.innerWidth)
    .height(350)
    .dimension(dateHub)
    .group(dateHubs)
    .x(d3.scale.linear().domain([minHub, maxHub]))
    .elasticY(true)
    .elasticX(true)
    .brushOn(false);

hubChart.on("preRedraw", function (chart) {
    chart.rescale();
});
hubChart.on("preRender", function (chart) {
    chart.rescale();
});

hubChart.onClick = function(chart){
    console.log(true);
}

hubChart.on("click", function (chart) {
    console.log(true);
});

hubChart.render();
