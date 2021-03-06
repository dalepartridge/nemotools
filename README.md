# nemotools
Collection of functions to use for python with NEMO

## Usage
### grid.py
A grid file, containing lat, lon, lengths and masks for the T/U/V grids can be loaded into 
<pre><code>import nemotools as nt
g = nt.grid('mesh_mask.nc')
</pre></code>
    
Additionally the bathymetry can be loaded via a separate file by specifying the filename and variable name (if different from default 'bathymetry')
<pre><code>g = nt.grid('mesh_mask.nc',bathfile='bathy.nc')</pre></code>

The full 3D thickness and depth variables can either be loaded at initialisation or at a later time using
<pre><code>g.load_thick()
g.load_depth()
</pre></code>

The area of each grid cell can be calculated for each of the 3 grids T/U/V (default T-grid)
<pre><code>g.area()</pre></code>

### mask.py
Sometimes domains are divided up into regions and are described using a field of zone indicators. By masking analysis can be restricted to an area(s). The mask_from_array function allows a quick and easy way to achieve this. For example, to create a mask everywhere the field is indicated with a 1,2 or 3 you can use:
<pre><code>field_mask = nt.mask.mask_from_array(field,flags=np.array([1,2,3]))</pre></code>
