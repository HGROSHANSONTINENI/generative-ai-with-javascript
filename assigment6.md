
function calculateDistance(lat1, long1, lat2, long2) {
    return Math.sqrt((lat2 - lat1) ** 2 + (long2 - long1) ** 2);
}

function getGpsPosition() {
    return { lat: 7.5, long: 134.5 };
}

function getWeatherForecast(lat, long) {
    return "Sunny";
}


const tools = {
    calculateDistance,
    getGpsPosition,
    getWeatherForecast
};

async function callTool(toolName, ...args) {
    if (tools[toolName]) {
        return tools[toolName](...args);
    } else {
        throw new Error(`Tool ${toolName} is not registered.`);
    }
}

(async () => {
    console.log("Testing getGpsPosition...");
    const gps = await callTool("getGpsPosition");
    console.log("GPS Position:", gps);

    console.log("Testing calculateDistance...");
    const distance = await callTool("calculateDistance", gps.lat, gps.long, 10, 140);
    console.log("Distance to (10, 140):", distance);

    console.log("Testing getWeatherForecast...");
    const weather = await callTool("getWeatherForecast", gps.lat, gps.long);
    console.log("Weather at current location:", weather);
})();