## AGS Experiments

Standalone web form which calls agsapi.bgs.ac.uk

<div>
<section id="identification">
    <h1>pyagsapi: AGS File Utilities Tool and API</h1>
    <br>
    <p>This tool and associated <a href="/docs/">API</a> allow schema validation, data validation and conversion of your <a href="https://www.ags.org.uk/data-format/">AGS files</a>.</p>
      <ul>
        <li>Accepts multiple AGS files. (Hold down <b>Ctrl</b> key to select more than one file)</li>
        <li>Tests AGS versions 4.x only</li>
        <li>Files are not saved or stored by this tool</li>
      </ul>
    <h2>Tools</h2>
    <ul>
        <li><a href="#validator">Schema & Data Validator</a></li>
        <li><a href="#converter">File Conversion .ags <--> .xlsx</a></li>
        <li><a href="#openapi">OpenAPI Documentation</a></li>
    </ul>
</section>
<br>
<hr>
<section id="validator">
    <br>
    <h2>AGS Schema & Data Validation</h2>
    <form action="https://agsapi.bgs.ac.uk/validate/" enctype="multipart/form-data" method="post">
        <p>Select AGS version, if not specified in TRAN_AGS: </p>
        <p>Tool uses AGS version specified in the supplied file, if not present, uses selection here, default is v4.0.4</p>
      </div>
      <br><br>
      <fieldset>
          <legend>Select Version</legend>
          <input type="radio" id="4.0.3" name="std_dictionary" value="v4_0_3">
          <label for="4.0.3">4.0.3</label>
          <input type="radio" id="4.0.4" name="std_dictionary" value="v4_0_4" checked>
          <label for="4.0.4">4.0.4</label>
          <input type="radio" id="4.1" name="std_dictionary" value="v4_1">
          <label for="4.1">4.1</label>
      </fieldset>
        <br>
      <fieldset>
        <legend>Select checkers</legend>
        <input type="checkbox" id="ags_validate" name="checkers" value="ags" checked>
        <label for="ags_validate"> I would like to run AGS schema validation</label><br>
        <input type="checkbox" id="bgs_validate" name="checkers" value="bgs" checked>
        <label for="bgs_validate"> I would like to run BGS data validation</label><br>
      </fieldset>
        <br>
      <fieldset>
          <legend>Select response format:</legend>
          <input type="radio" id="text" name="fmt" value="text">
          <label for="text">Plain Text</label>
          <input type="radio" id="json" name="fmt" value="json" checked>
          <label for="json">JSON</label><br>
      </fieldset>
        <br>
      <fieldset>
          <legend>Select .ags file(s) for validation (v4.x only). and submit</legend>
          <input name="files" type="file" multiple>
          <input type="submit">
      </fieldset>
    </form>
    <h2>AGS Validation</h2>
    <p>Performs validation using the <a href="https://gitlab.com/ags-data-format-wg/ags-python-library.">Official AGS Python Library</a> which implements checks of the rules as written in the AGS data format standard v4.x</p>
    <h2>BGS Data Validation</h2>
      <p>Data validation against the National Geoscience Data Repository requirements</p>
      <h3>Validation rules</h3>
        <p>Your files will be validated against the following rules as defined by BGS/NGDC:</p>
        <ul>
          <li>Check required Groups</li>
            <ul>
              <li>Groups shall include PROJ, LOCA or HOLE, ABBR, TYPE, UNIT</li>
            </ul>  
            <li>Check required BGS Groups</li>
              <ul>
                <li>Groups may include GEOL - required for BGS submission</li>
              </ul>
            <li>Check Spatial Referencing</li>
              <ul>
                <li>Spatial referencing system defined in LOCA_GREF, LOCA_LREF or LOCA_LLZ.</li> 
                <li>Example: LOCA_GREF:OSGB, LOCA_LREF:London Grid 1, LOCA_LLZ:WGS84</li>
              </ul>
            <li>Check Easting/Northing present.</li>
              <ul>
                <li>LOCA_NATE and LOCA_NATN are populated. Zeros or null do not pass</li>
              </ul>
            <li>Check Easting/Northing values fall within reasonable range</li>  
              <ul>
                <li>LOCA_NATE values inside 100,000 to 800,000 range</li>
                <li>LOCA_NATN values inside 100,000 to 1,400,000 range</li>
              </ul>
            <li>Check Drill Depth  (HDPH) present</li>
              <ul>
                <li>HDPH_TOP does not contain null values</li>
                <li>HDPH_BASE does not contain zero or null values</li>
              </ul>
            <li>Check Drill depths (HDPH) have corresponding records in GEOL table</li>
              <ul>
                <li>Checking HDPH LOCA_IDs are in GEOL group AND GEOL LOCA_IDs are in HDPH group</li>
              </ul>
            <li>Check locations are onshore Great Britain or Northern Ireland</li>
              <ul>
                <li>Note: If using Irish grid and GREF not entered, tool cannot differentiate from EPSG:27700 (OSGB)</li>
              </ul>
            <li>Check for duplication between NATE/NATN, LOCX/LOCY and LON/LAT</li>
              <ul>
                <li>Duplication presumes error in these columns which should be checked</li>
              </ul>
            <li>Check LOCA_ID references are valid</li>
              <ul>
                <li>Checks all groups which have LOCA_ID are populated with a valid record present in the LOCA Group.</li>
              </ul>      
        </ul>
</section>
<br>
<hr>
<section id="converter">
    <h2>AGS Converter</h2>
      <div class="tooltip"><p>Convert .ags file(s) to/from .xlsx.</p>
        <span class="tooltiptext">Which ever format file is submitted, the opposite will be returned e.g. if 5 .ags files and 3 .xlsx files were submitted the result would be 5 .xlsx files and 3 .ags files</span>
      </div>
      <br>
    <br>
    <fieldset>
        <legend>Select files</legend>
    <form action="https://agsapi.bgs.ac.uk/convert/" enctype="multipart/form-data" method="post">
    <input name="files" type="file" multiple>
    <input type="submit">
    </fieldset>
    </form>
</section>


