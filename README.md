# DualSPHysics_2
CaseFlowCylinderRe200 when modifying the geometry I got an error

Greetings to all, I have had an error for days and I have changed several parameters of the geometry but I still get the error : *** Exception (JXml::ErrReadAtrib) at DualSPHysics/source/JXml.cpp:257
Text: Error reading xml - Value of 'mkfluid' invalid. No particles data with mkfluid=1 to define inout points.
File: CaseFlowCylinder_Re200_out/CaseFlowCylinder_Re200.xml(row:116)
I would like someone to guide me on how to overcome this error, thank you here my model 
in the geometry:

<speedsound value="15" auto="false" comment="Speed of sound to use in the simulation (by default speedofsound=coefsound*speedsystem)" />
            <hdp value="2" comment="Alternative option to calculate the smoothing length (h=hdp*dp)" />
            <cflnumber value="0.2" comment="Coefficient to multiply dt" />
        </constantsdef>
        <mkconfig boundcount="240" fluidcount="4" />
        <geometry>
            <definition dp="0.000110">
                <pointmin x="0" y="0" z="0" />
				<!-- coordenadas de esquina inferior izq. -->
                <pointmax x="0.012" y="0" z="0.0041" />
				<!-- coordenadas de esquina superior derecha. -->
            </definition>
            <commands>
                <mainlist>
                    <setshapemode>dp | bound</setshapemode>
					<!-- la zona del fluido. -->
                    <setdrawmode mode="full" />
                    <!-- FLUID DOMAIN -->
                    <setmkfluid mk="0" />
                    <drawbox>
                        <boxfill>solid</boxfill>
                        <point x="0" y="0" z="0.0002" />
						<!-- punto inicial de mi fluido -->
                        <size x="0.012" y="0" z="0.0037" />
						<!-- dimensiones de mi fluido. -->
                    </drawbox>
                    <!-- OPEN BOUNDARIES -->
					<!-- la frontera de la caja -->
                    <setmkfluid mk="1" />
                    <drawbox>
                        <boxfill>left</boxfill>
                        <point x="0" y="0.00001" z="0.0002" />
						<!-- punto inicial de mi fluido -->
                        <size x="0.012" y="0.00001" z="0.0037" />
						<!-- dimensiones de mi fluido. -->
                    </drawbox>
                    <setmkfluid mk="2" />
                    <drawbox>
                        <boxfill>right</boxfill>
                        <point x="0" y="0.00001" z="0.0002" />
						<!-- <!--punto inicial de mi fluido -->
                        <size x="0.012" y="0.00001" z="0.0037" />
						<!-- <!--dimensiones de mi fluido. -->
                    </drawbox>
                    <!-- CYLINDER -->
                    <setmkbound mk="0" />
                    <drawcylinder radius="0.001100">
                        <point x="0.004" y="-0.001300"	z="0.003175" />
						<!-- Deforma -->
                        <point x="0.008" y="0.001300" z="0.003185" />
						<!-- Desplaza -->
                    </drawcylinder>
				    <!-- SOLID BOUNDARY -->
					<!-- la caja en 2D -->
                    <setmkbound mk="1" />
                    <drawbox>
                        <boxfill>solid</boxfill>
                        <point x="0" y="0" z="0" />
						<!-- coordenada inicial de la frontera.izquierda inferior. -->
                        <size x="0.015" y="0.0001" z="0.0002" />
						<!-- Dimensiones de la caja -->
                    </drawbox>
                    <setmkbound mk="2" />
                    <drawbox>
                        <boxfill>solid</boxfill>
                        <point x="0" y="0" z="0.0039" />
						<!-- <!--coordenadas final de la frontera.superior derecha. -->
                        <size x="0.015" y="0" z="0.0002" />
						<!-- <!--Dimensiones de la caja -->
                    </drawbox>
                    <!-- END -->	
                </mainlist>
            </commands>
        </geometry>

