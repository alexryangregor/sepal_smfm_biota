SMFM Biota
==========

The BIOTA tool is part of the Satellite Monitoring for Forest Management (SMFM) project by the World Bank, and it was developed by `LTS International <https://ltsi.co.uk/>`_ and the `University of Edinburgh <https://www.ed.ac.uk/geosciences>`_ with an integration in the SEPAL platform developed by the SEPAL developer team. The tool relies on the use of JAXA's `ALOS PALSAR <https://www.eorc.jaxa.jp/ALOS/en/about/palsar.htm>`_ L-band mosaics and it allows you to produce outputs of:

-   Calibrated Gamma0 backscatter
-   Forest cover
-   Above-ground biomass
-   Above-ground biomass change
-   Classified forest change types (deforestation, degradation, etc)

More information can be found online at https://www.smfm-project.com/.

In this exercise, you will learn how to use the BIOmass Tool for Alos (BIOTA) to calculate above-ground biomass in dry forests and savannas, as well as change maps.


.. note::

    **objectives**:

    -   Generate maps of above-ground biomass (AGB), Gamma0 backscatter, forest cover, AGB change, deforestation risk, and change type. 

.. warning::

    **Prerequisites**: 

    -   SEPAL account

Navigate to the **Apps** menu by clicking on the wrench icon and typing "SMFM" into the search field. Select "SMFM Biota".

.. note::

    Sometimes the tool takes a few minutes to load. Wait until you see the tool's interface. In case the tool fails to load properly, as seen below, please close the tab and repeat the above steps. If this does not work, reload SEPAL.

    .. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_fail.png
        :alt: Failure of the BIOTA tool.
        :align: center
        :width: 600
        

    If none of these steps work, you might need to start another instance. Please see `Introduction to SEPAL <https://docs.sepal.io/en/latest/setup/presentation.html#terminal-tab>`_ for steps on how to use the terminal to start a higher instance. A 'm4' instance should be enough.

You should see an interface like the one below. 

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_interface.png
    :alt: The SMFM BIOTA interface.
    :align: center
    :width: 600

.. tip::

    Depending on your computer screen size, sometimes the left column will be on top of the content, as seen below:

    .. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_column.png
        :alt: Left column on top of the tool.
        :align: center
        :width: 600

    If this is the case, you can:
    
    -   Adjust your browser zoom level, or

    .. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_chrome.png
        :alt: Example of how to adjust the zoom level on Google Chrome.
        :align: center
        :width: 600

    -   Keep the zoom level but click outside of the column to hide it. Then, to open it again, you will need to click on the three dots located at the top right side.

    .. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_three_dots.png
        :alt: How to show the left column again.
        :align: center
        :width: 600

Downloading the ALOS mosaics
""""""""""""""""""""""""""""

The first step is to select the parameters for accessing data from ALOS (JAXA). The data is delivered in either 1x1 degree tiles or 5x5 degree collections of tile into SEPAL.

Under :code:`Required Inputs` you need the define Latitude and Longitude coordinates. To do so, click on your point of interest on the map that is shown on the right side - this will be the upper-left coordinate of the tiles. The default values are -75 degrees for Longitude and 0 degrees for Latitude. For this exercise, we will demonstrate the steps for Tanzania (Latitude -2.54, and Longitude 31.04 - a point in-between the Moyowosi Game Reserve and the Kigosi Game Reserve, next to the border of the Getta and Kigoma regions).

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_map.png
    :alt: Selecting a point on the map.
    :align: center
    :width: 600

.. note::

    The BIOTA tool was designed for woodlands and dry forests as it uses a generic equation to calibrate Gamma0 backscatter to forest AGB developed using forest plot data from Mozambique, Tanzania, and Malawi, in southern Africa. For global applicability, the tool supports the calibration of country-specific backscatter-AGB relationships through determined parameters that will be explained later.

Next, we define the two years of interest. For this exercise, we will leave the default values, 2016 for Year 1 and 2017 for Year 2. Year 2 is used for calculating changes.

The tool gives you the option to choose either 1x1 or 5x5 degree tile size. We will select 1x1 tile size for time purposes.

Before selecting :code:`Download Images`, we will look into the :code:`Optional Inputs` tab.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_optional_inputs_tab.png
    :alt: Location of the optional inputs tab.
    :align: center
    :width: 600

Different parameters can be changed here. These include the parameters that should be calibrated according to your area of interest and specific forest characteristics. Default values are specific to southern African forests.

.. csv-table::
    :header: Parameter, Role

    Lee filter, Applies a Lee filter to the data. This reduces inherent speckle noise in SAR imagery. Uncheck if you do not want the filter applied.
    Window size, Lee filter window size. Defaults to 5 x 5 pixels.
    Downsample factor, Applies downsampling to inputs by specifying an integer factor to downsample by. Defaults to 1 - no downsampling.
    Forest threshold, A forest AGB threshold (in tonnes per hectare) to separate forest from non-forest (specific to your location). Defaults to 10 tC/ha.
    Area threshold, A minimum area threshold (in hectares) to be counted as forest (e.g. a forest patch must be greater than 1 ha in size). Defaults to 0 ha.
    Change area threshold, A threshold for a minimum change in forest area required to be flagged as a change. Defaults to 2 ha. This is for users who aim to produce change maps. 
    Change magnitude threshold, The minimum absolute change in biomass (in tonnes per hectare) to be flagged as a change. Defaults to 15 tC/ha.This is for users who aim to produce change maps.
    Contiguity, The criterion of contiguity between two spatial units. The rook criterion defines neighbors by the existence of a common edge between two spatial units. The queen criterion is somewhat more encompassing and defines neighbors as spatial units sharing a common edge or a common vertex.
    Polarisation, Which SAR polarisation to use. Defaults to HV.


We will leave the parameters with default values.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_optional_inputs.png
    :alt: Optional parameters screen.
    :align: center
    :width: 600

Now, go back to the :code:`Required Inputs` tab and click :code:`Download Images` at the bottom. This will download all ALOS data tiles into your SEPAL account.

.. note::

    Depending on your point coordinates, it may take a significant amount of time before your data finish downloading. For the point in Tanzania, it should take about 5 minutes.

You can see the status of the downloads at the bottom of the page.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_download_status.png
    :alt: Status about the download.
    :align: center
    :width: 600

Once the downloads are finalized for both years, you are able to see the downloaded files under the SEPAL :code:`Files`. Go to :code:`module_results` > :code:`smfm` > :code:`data`. 

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_files.png
    :alt: SEPAL Files with downloaded data.
    :align: center
    :width: 600

Here is a demonstration of the above steps:

.. youtube:: d759Aqi85HE
    :height: 315
    :width: 560

Processing the data and producing outputs
"""""""""""""""""""""""""""""""""""""""""

Now that the download finished, we can process the data to produce the desired outputs.

Click on the :code:`Process` tab on the left side.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_process.png
    :alt: BIOTA Process window.
    :align: center
    :width: 600

For Year 1, we will choose "Forest property" - this will automatically check all outputs available ("Gamma0", "Biomass", "Forest Cover"). For Year 2 we will choose "Forest Change" (changes between 2016 and 2017), which will also select all available outputs ("Biomass change", "Change type", "Deforestation risk"). These will be explained later. Now, click on :code:`Get Outputs` to start the processes.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_process_get.png
    :alt: Select outputs and start the process by clicking on "Get outputs".
    :align: center
    :width: 600

.. note::

    Depending on your point coordinates, it may take a significant amount of time before your data finish downloading. For the point in Tanzania, it should take about 2 minutes.

Similarly to before, the tool will show the process status at the bottom. You will also note a change of color from white to yellow next to each output. White means not started, Yellow means processing and Green means finalized.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_output_processing.png
    :alt: Status of outputs.
    :align: center
    :width: 600

Once done, you will see a message similar to the one below, and all outputs will have a green "light". 

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_output_done.png
    :alt: Process finalized.
    :align: center
    :width: 600

Here is a demonstration of the above steps:

.. youtube:: OMGESeERRGo
    :height: 315
    :width: 560

Displaying your outputs
"""""""""""""""""""""""

With the outputs processed, we can now visualize the results.

On the same window, under :code:`Display Outputs`, you can select the process to display by clicking on the dropdown 'Select process' option.

First select Biomass. Then press :code:`Display`. You will see the map pop up on your screen:

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_display.png
    :alt: Biomass map.
    :align: center
    :width: 600

This is showing above-ground biomass in tonnes per hectare (tC/ha) for the 1x1 degree tile in Tanzania. To go back to the interface and select the other outputs, you can click anywhere on the screen outside of the map and do the same for the other results.

If you followed these exact steps, your outputs should look similar to the ones below: 

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_all.png
    :alt: BIOTA outputs for Tanzania.
    :align: center
    :width: 600

A summary of each output is described in the table below:

.. csv-table::
    :header: Output, Description

    Gamma0, Gamma0 backscatter in decibels for the polarization specified
    Biomass, Biomass in tonnes per hectare
    Forest/Woody cover, Binary classification of forested (1) and non-forested (0) areas
    Change type, Change described in 7 different types. They are specified below
    Biomass change, Change in biomass in tonnes per hectare
    Deforestation risk, Risk of deforestation from Low (1) to High (3) 
    
There are 7 change types described in the BIOTA tool, each of which is defined as a number 0 to 6 and color-coded on the map. Change types are:

.. csv-table::
    :header: Change class, Pixel value, Description

    Deforestation, 1, A loss of AGB from that crosses the ``forest_threshold``.
    Degradation, 2, A loss of AGB in a location above the ``forest_threshold`` in both images.
    Minor Loss, 3, A loss of AGB that does not cross the ``change_area_threshold`` or ``change_magnitude_threshold``.
    Minor Gain, 4, A gain of AGB that does not cross the ``change_area_threshold`` or ``change_magnitude_threshold``.
    Growth, 5,A gain of AGB in a location above the ``forest_threshold`` in both images.
    Afforestation, 6, A gain of AGB that crosses the ``forest_threshold``.
    Nonforest, 0, Below ``forest_threshold`` in both images.

You can also use the :code:`Write Raster` option to save this map into your SEPAL account. Once you click on `Write Raster` you should see a message in green informing that your export has been completed.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_export.png
    :alt: Map export complete for the Change type output.
    :align: center
    :width: 600

Then, the file will be located in your SEPAL Files. You can download this map by selecting it and clicking on the Download button at the top right corner. This will download the output as a TIF file that can be used in a GIS software.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_export_file.png
    :alt: Exported map in the Files.
    :align: center
    :width: 600

Here is a demonstration of the above steps:

.. youtube:: my8U5TaV9IU
    :height: 315
    :width: 560

Additional Resources
""""""""""""""""""""

On the left side, you can access:

-   Source code: this takes you to the source code of the tool, which is a GitHub repository.
-   Wiki: the "README" file of the tool, you can find additional information and instructions about how to use the tool.
-   Bug report: in case you notice a bug or have issues using the tool, use this option to report the bug or issue. This will take you to an issue creation page on the GitHub repository of the tool.

.. figure:: https://raw.githubusercontent.com/dfguerrerom/sepal_smfm_biota/main/doc/_img/biota_resources.png
    :alt: Additional Resources.
    :align: center
    :width: 600
