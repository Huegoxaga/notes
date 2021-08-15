# Electricity & Magnetism

* Electric Charges
  * Same type of charges repel each other, opposite charges attract each other.
  * Proton
    * It has a positive electric charge. It has one elementary positive charge, denoted as `+1e` or ![$+1q\_e$](https://render.githubusercontent.com/render/math?math=%24%2B1q_e%24).
    * The mass of a proton is ![$1.672 : 621 : 923 : 69 \times 10^{-27}$](https://render.githubusercontent.com/render/math?math=%241.672+%5C%3A+621+%5C%3A+923+%5C%3A+69+%5Ctimes+10%5E%7B-27%7D%24) `kg`.
  * Electron
    * It has a negative electric charge. It has one elementary positive charge, denoted as `-1e` or ![$-1q\_e$](https://render.githubusercontent.com/render/math?math=%24-1q_e%24).
    * The mass of a proton is ![$9.109 : 383 : 701 : 528 \times 10^{-31}$](https://render.githubusercontent.com/render/math?math=%249.109+%5C%3A+383+%5C%3A+701+%5C%3A+528+%5Ctimes+10%5E%7B-31%7D%24) `kg`.
  * Unit - Coulomb `C`
    * Defined as the amount of electric charge transported by a constant electric current of one ampere in one second.
    * Each elementary electric charge has the value of ![$1.602176634 \times 10^{-19}$](https://render.githubusercontent.com/render/math?math=%241.602176634+%5Ctimes+10%5E%7B-19%7D%24) `C`.
  * Coulomb's Law
    * The force between two charges are defined as ![$F = k \frac{Q\_1 Q\_2}{R^2}$](https://render.githubusercontent.com/render/math?math=%24F+%3D+k+%5Cfrac%7BQ_1+Q_2%7D%7BR%5E2%7D%24) where `k` or ![$k\_e$](https://render.githubusercontent.com/render/math?math=%24k_e%24) is the Coulomb constant ![$k\_e = \frac{1}{4 \pi \epsilon\_0}$](https://render.githubusercontent.com/render/math?math=%24k_e+%3D+%5Cfrac%7B1%7D%7B4+%5Cpi+%5Cepsilon_0%7D%24) and ![$ k\_e \approx 9 \times 10^{9} N \cdot m^2 \cdot C^{-2}$](https://render.githubusercontent.com/render/math?math=%24+k_e+%5Capprox+9+%5Ctimes+10%5E%7B9%7D+N+%5Ccdot+m%5E2+%5Ccdot+C%5E%7B-2%7D%24).
    * ![$ \epsilon\_0 $](https://render.githubusercontent.com/render/math?math=%24+%5Cepsilon_0+%24) is called vacuum permittivity or permittivity of free space, ![$ \epsilon\_0 = \frac{1}{\mu\_0 c^2} \approx 8.85418781762039 \times 10^{-12}$](https://render.githubusercontent.com/render/math?math=%24+%5Cepsilon_0+%3D+%5Cfrac%7B1%7D%7B%5Cmu_0+c%5E2%7D+%5Capprox+8.85418781762039+%5Ctimes+10%5E%7B-12%7D%24)`F/m`.
  * `λ` is often used to represent linear charge density with the unit as `C/m`
  * `σ` represents charge density of a surface with unit as `C/m^2`
    * Charges alway distributed on the surface of a conductor.
* Electric Field
  * A single or a group of electric charge can form a electric field around it. Any additional charge goes into the field will have a force on it.
  * For a field diagram dot means outwards, cross means inwards. similar to an arrow.
  * The strength of a electric field\(`E`\) is defined as `F/Q` where `Q` is the amount of charges the change contain in Coulomb\(`C`\).
    * `E` is a vector as ![$\overrightarrow{E}$](https://render.githubusercontent.com/render/math?math=%24%5Coverrightarrow%7BE%7D%24) when considering the direction of it.
  * The strength of the electric field `E` also equals to `V/d` which is the potental difference divided by the distance.
  * Arrow can be drawn to represtion the direction of the field, it is the same direction as the forces applied on a positive charge at this location.
  * A Uniform Electric Field has same ![$\overrightarrow{E}$](https://render.githubusercontent.com/render/math?math=%24%5Coverrightarrow%7BE%7D%24) at any point in the field.
  * Gauss's Law - It uses an area of interest to calculate electric field. The area of interest is a sphere\(Gaussian Surface\) around a charged object with same strength of electric field.
    * ![$\oint \overrightarrow{E} d\overrightarrow{A} =\oint EdA \cos{\theta} = \frac{Q\_{ENCLOSED}}{\epsilon\_0}$](https://render.githubusercontent.com/render/math?math=%24%5Coint+%5Coverrightarrow%7BE%7D+d%5Coverrightarrow%7BA%7D+%3D%5Coint+EdA+%5Ccos%7B%5Ctheta%7D+%3D+%5Cfrac%7BQ_%7BENCLOSED%7D%7D%7B%5Cepsilon_0%7D%24) where `A` is the Gaussian surface. `Q` is the total amount of charges contained in the Gaussian surface.
    * The product `EAcosθ` also equals to the Electric Flux `ϕ`.
* Electrical Potential
  * The potential difference between two points `ΔV` equals `W/Q` where `W` is the work that required to move the charage from one location to the other.
  * The electric potential of a charge `Q` at location that is `R` meter away is `V = kQ/R`. The potential difference from infinity to `R` meter away of the change is `V`.
    * This result can be derived when integrate `dW` and `dR`, using an imaginary charged which will be moved from infinity to location `R`.
  * To calculate the amount of work needed to place individual charges in specific location can be solved by placing one charge at a time and add the total work required.
* Capacitors & Capacitance
  * Capacitor is a electrical componenet that can hold charge, capacitance describes the capacity of the capacitor.
    * When the capacitor is connected to a power source for a while it is charged, the charges on the plates will remain the same when it is disconnected to the power source.
  * Capcitors are depicted as two parallel metal plate with each plate connected to one side of the power source.
  * The capacitance `C = Q/V` where Q is the amount of charges it holds and `V` is the voltage between each plate.
  * `F` is the unit for capacitance, Unit `F` times unit `V` returns the charge unit coloumb `C`.
  * The dielectric is the medium in between two plates. It is associated with a dielectric constant `k`. It determines the capacitance of a capatior, ![$C = \epsilon\_0 k \frac{A}{d}$](https://render.githubusercontent.com/render/math?math=%24C+%3D+%5Cepsilon_0+k+%5Cfrac%7BA%7D%7Bd%7D%24) where `A` is the plate size, `d` is the distance between the plates.
    * `k = 1` when no dielectric\(air\) is inserted in between.
  * When capacitors connected in series in a circuit, they will be equivalent to a singe capacitor with capacitance equals the sum of the capacitance of all the connected capacitors.
  * When capcaitors connected in parallel, the total capacitance equals to ![$C\_T = \frac{1}{C\_1}+ \frac{1}{C\_2} + \frac{1}{C\_3} + \cdots$](https://render.githubusercontent.com/render/math?math=%24C_T+%3D+%5Cfrac%7B1%7D%7BC_1%7D%2B+%5Cfrac%7B1%7D%7BC_2%7D+%2B+%5Cfrac%7B1%7D%7BC_3%7D+%2B+%5Ccdots%24)
* Resistor
  * The resistivity is the level of resistence of a material when conducting electricity. The unit for resistivity is `Ωm`.
  * The resistance of any material can be calculated by `R = 𝜌 * L / A` where `𝜌` is the resistivity of the material, `L` is the length, and `A` is the cross section area.
  * The drift velocity describes the speed that a charge travels in a conductor, It has the relationship that `I = dQ/dt = n|q|vA` where `n` represents the number of free charges in a certain material and `A` is the cross section area of the conductor.
    * In reality, the drift velocity is very slow.
  * When resistor connected in series in a circuit, they will be equivalent to a single resistor with resistence equals the sum of the resistence of all the connected resistors.
  * When resistor connected in parallel, the total resistence equals to ![$R\_T = \frac{1}{R\_1}+ \frac{1}{R\_2} + \frac{1}{R\_3} + \cdots$](https://render.githubusercontent.com/render/math?math=%24R_T+%3D+%5Cfrac%7B1%7D%7BR_1%7D%2B+%5Cfrac%7B1%7D%7BR_2%7D+%2B+%5Cfrac%7B1%7D%7BR_3%7D+%2B+%5Ccdots%24)
    * The current will be split, resistor with lower resistence will have larger current. The current is determined by ![$I\_{Total} \left\( \frac{R\_{AllOther}}{R\_{Total}} \right\)$](https://render.githubusercontent.com/render/math?math=%24I_%7BTotal%7D+%5Cleft%28+%5Cfrac%7BR_%7BAllOther%7D%7D%7BR_%7BTotal%7D%7D+%5Cright%29%24)
  * Ohm's Law - `I = V / R`
* Magnetic Field
  * The unit of magnetic field is Tesla, denoted as `T`.
  * Charges moves in the magnetic field will have a force on it, `F=qvBsinθ` where `θ` is the angle between the moving direction of `v` and the direction of the magenetic field with strength `B`.
    * If `v` and `B` are represented as vectors use cross product of matrix `v` times matrix `B`.
    * The direction of the force is determines using right hand rules for positive charges and left hand rule for negative charges. Fingers allign with the direction of `v` and the hand curls to the direction of the magnetic field. the thumb will point to the direction of the force.
    * The left or right hand rules still work when the `v` and `B` does not have 90 degrees angle, curl the hands to the direction that has the smallest angle with `v`.
  * Moving charges will have magnetic field around it,
    * The direction of the magnetic for positive charges can be determined using right hand rule, thumb points to the direction of the moving charges. the fingers curls towards the direction of the magnet field.
    * Ampere's Law can be used to calculate the magnitude of the magnetic field. In general, ![$\oint \overrightarrow{B} \cdot d \overrightarrow{l} = \mu\_0 I\_{ENCLOSED}$](https://render.githubusercontent.com/render/math?math=%24%5Coint+%5Coverrightarrow%7BB%7D+%5Ccdot+d+%5Coverrightarrow%7Bl%7D+%3D+%5Cmu_0+I_%7BENCLOSED%7D%24) where ![$\mu\_0 = 4 \pi \times 10^{-7} ; \frac{Tm}{A}$](https://render.githubusercontent.com/render/math?math=%24%5Cmu_0+%3D+4+%5Cpi+%5Ctimes+10%5E%7B-7%7D+%5C%3B+%5Cfrac%7BTm%7D%7BA%7D%24). For different sources of the field according to Ampere's law:
      * Particles: The magnitude of the field can be ![$\|\overrightarrow{B}\| = \frac{\mu\_{0}qv \sin{\theta}}{4 \pi r^2}$](https://render.githubusercontent.com/render/math?math=%24%7C%5Coverrightarrow%7BB%7D%7C+%3D+%5Cfrac%7B%5Cmu_%7B0%7Dqv+%5Csin%7B%5Ctheta%7D%7D%7B4+%5Cpi+r%5E2%7D%24) where `r` is the distance to the point of the magnetic field, `θ` is the angle between the magnetic field and the charges moing direction.
        * Alpha particle: 2 protons and 2 neutrons. It has +2e charges.
      * Wire segment: The magnitude of the field can evaluated using the Biot & Savart Law, ![$\|\overrightarrow{B}\| = \frac{\mu\_{0}I l \sin{\theta}}{4 \pi r^2}$](https://render.githubusercontent.com/render/math?math=%24%7C%5Coverrightarrow%7BB%7D%7C+%3D+%5Cfrac%7B%5Cmu_%7B0%7DI+l+%5Csin%7B%5Ctheta%7D%7D%7B4+%5Cpi+r%5E2%7D%24) where `l` is the wire segment length and `θ` is the angle between the wire and the magnetic field.
    * Magnetic flux `ϕ` equals the Magnetic field times area `A`.

