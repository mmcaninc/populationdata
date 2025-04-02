<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Colorado Springs Population Data</title>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css?family=Roboto:400,500,700" rel="stylesheet">
  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
        integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
  <!-- Leaflet JavaScript -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
          integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>
  <style>
    /* Global Styling */
    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(to right, #f0f2f0, #000c40);
      margin: 0;
      padding: 0;
      color: #333;
    }
    /* Header Styling */
    header {
      background: linear-gradient(to right, #00416a, #e4e5e6);
      color: #fff;
      text-align: center;
      padding: 40px 20px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }
    header h1 {
      font-size: 3em;
      margin: 0;
    }
    header p {
      font-size: 1.3em;
      margin-top: 10px;
    }
    /* Section Styling */
    section {
      max-width: 1000px;
      margin: 20px auto;
      background-color: rgba(255,255,255,0.9);
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    section p {
      font-size: 1.1em;
      line-height: 1.6;
    }
    /* Map Styling */
    #map {
      height: 500px;
      width: 100%;
      border: 3px solid #00416a;
      border-radius: 8px;
      margin-top: 20px;
    }
    /* Footer Styling */
    footer {
      background-color: #00416a;
      color: #fff;
      text-align: center;
      padding: 15px;
      margin-top: 20px;
    }
    /* Legend Styling */
    .legend {
      background: white;
      padding: 6px 8px;
      font: 14px Arial, Helvetica, sans-serif;
      border-radius: 5px;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
      line-height: 18px;
      color: #555;
    }
    .legend h4 {
      text-align: center;
      margin: 2px 12px 8px;
      font-weight: 700;
    }
  </style>
</head>
<body>
  <header>
    <h1>Colorado Springs Population</h1>
    <p>US Census 2020 Data – Represented with Scaled Circles</p>
  </header>
  <section>
    <p>This interactive map covers Colorado Springs. The circles represent approximate population counts for different regions of the city, with larger circles indicating higher populations. Data is based on the 2020 US Census (approximate values for demonstration).</p>
    <div id="map"></div>
    <div class="legend" id="legend">
      <h4>Population Legend</h4>
      <p><strong>Circle Radius (meters)</strong> is roughly proportional to population:</p>
      <ul>
        <li>~500 m: ~40,000 residents</li>
        <li>~700 m: ~60,000 residents</li>
        <li>~900 m: ~80,000 residents</li>
      </ul>
    </div>
  </section>
  <footer>
    <p>&copy; 2025 [Michael McAninch]. All rights reserved.</p>
  </footer>
  <script>
    // Initialize the map centered on Colorado Springs
    var map = L.map('map').setView([38.8339, -104.8214], 11);

    // Add the OpenStreetMap tile layer
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 18,
      attribution: 'Map data &copy; <a href="https://www.openstreetmap.org">OpenStreetMap</a> contributors'
    }).addTo(map);

    // Define regions with approximate center coordinates and population (from US Census 2020 approximations)
    var regions = [
      {
        name: "Downtown Colorado Springs",
        coords: [38.8339, -104.8214],
        population: 40000,  // approximate
        radius: 500
      },
      {
        name: "North Colorado Springs",
        coords: [38.9200, -104.8214],
        population: 60000,  // approximate
        radius: 700
      },
      {
        name: "West Colorado Springs",
        coords: [38.8400, -104.9000],
        population: 80000,  // approximate
        radius: 900
      },
      {
        name: "Northeast Colorado Springs",
        coords: [38.9000, -104.7500],
        population: 75000,  // approximate
        radius: 800
      },
      {
        name: "Southwest Colorado Springs",
        coords: [38.7800, -104.8800],
        population: 65000,  // approximate
        radius: 700
      }
    ];

    // Loop through regions to create circles
    regions.forEach(function(region) {
      L.circle(region.coords, {
        color: '#FF5733',
        fillColor: '#FFBD69',
        fillOpacity: 0.5,
        radius: region.radius  // radius in meters (adjusted for demo)
      }).addTo(map)
      .bindPopup("<strong>" + region.name + "</strong><br>Approx. Population: " + region.population);
    });
  </script>
</body>
</html>
