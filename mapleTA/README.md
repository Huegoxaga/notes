MapleTA

for multiple choice, the first choice as a numeric value 1. second is 2 and so on.

if(Number, returnifnonzero, returnIfZero);

chained / from left to right

numfmt(“###,###.00”,  10000000);  //formatted output.

condition: le($A3,$A4);   a3 < a4

condition: ne($a,0);   not equal

decimal(3, 20.8571) // three decimal places.

returns 20.857

sig(3,3.23432)//three sig dig

int($x)   return the integer part of $x

random decimal to x sig  $test=rand(begin, stop , x);

eq(a, b), ge(a, b), le(a, b), ne(a, b)

for multiple choice that has two or more answers
use $AnsA,$AnsB in the Algorithmic Value Answers field.
checking correct answer still works if algorithmic value is set.

when multiple variables in one formula, the equation editor behave poorly.

###########################################################
#This will be used for all st nd rd cases in the future. for any given number $A, generate st nd rd for it as $tha
$st="st";
$nd="nd";
$rd="rd";
$th="th";
$tha=maple("if (modp($A,10)=1) then $st elif (modp($A,10)=2) then $nd elif (modp($A,10)=3) then $rd else $th end if");
$thb=maple("if (modp($B,10)=1) then $st elif (modp($B,10)=2) then $nd elif (modp($B,10)=3) then $rd else $th end if");
############################################################




ANSWER:=$ans;
evalb((ANSWER)-($RESPONSE)=0);

$a = range(-5,-2,1);

$n = range(2,5,1);

$q = '($a*t)^$n';

$qmath=mathml($q);   //convert expression io symbolic form.

$coef = ($a)^$n;

$ans=maple(“simplify($q)”);//simplify the expression

$q='$a1*x*y^$a2+$a13*x^2*y^$a21';
$mathmlq=mathml($q);
$ans=maple(“factor($q)");  //factorize the expression
$mathmlans=mathml($ans);

LOOK FOR IN ANSWER, LIST that must be there
ANSWER:=$ans;
evalb((ANSWER)=($RESPONSE) and not StringTools:-Search("$coef","$RESPONSE")=0 and not StringTools:-Search("x^$xe","$RESPONSE")=0 and not StringTools:-Search("y^$ye","$RESPONSE")=0 and not StringTools:-Search("z^$ze","$RESPONSE")=0);

r:="$RESPONSE";
is(parse(r)=$ans);
is and evalb are similar, but more lenient.
parse convert string to expression.

$a=range(3,5,1);

$b=range(2,4,1);

$c=range(3,5,1);

$d=range(4,6,1);


$e=range(2,5,1);

$q="($a*x^$b*y^$c*z^$d)^$e";

$qmathml=mathml($q);

$ans=maple("simplify($q)");

$coef=$a^$e;

$xe=$b*$e;

$ye=$c*$e;

$ze=$d*$e;

$ans1=$coef*x^$xe*y^$ye*z^$ze;

LOOK FOR IN ANSWER EITHER ONE MUST BE THERE:
ANSWER:=$ans;
evalb((ANSWER)=($RESPONSE) and not StringTools:-Search(["$den","$dec"],"$RESPONSE")=[0,0]);


COUNT UP A SPECIFIC STRING AND THE EXACT NUMBER MUST BE PRESENT
ANSWER:=$ans;
evalb((ANSWER)=($RESPONSE) and StringTools:-CountCharacterOccurrences("$RESPONSE","^")=3 );

CHANGE STUDENT RESPONCE FROM DECIMAL TO RATIONAL EQUVALENT:
convert(expr,rational);

use 3*x instead of 3x

evalb($ANSWER - convert($RESPONSE, rational) = 0);

evalb((ANSWER)=(convert($RESPONSE,rational)) and not StringTools:-Search("$coef","$RESPONSE")=0);

EXTRA GRADING CODE:
ANSWER:=$ans;
is(simplify((ANSWER)-($RESPONSE))=0);

LOOK FOR EXPONENT NUMBER AND A STRING (for strings if %coef=4 and a 4 is in the student responce say with 14 then a 4 is present
ANSWER:=$ans;
evalb((ANSWER)=($RESPONSE) and StringTools:-CountCharacterOccurrences("$RESPONSE","^")=2 and not StringTools:-Search("$coef","$RESPONSE")=0);

ANSWER:=$ans;
evalb(simplify((ANSWER)-($RESPONSE)) and StringTools:-CountCharacterOccurrences("$RESPONSE","^")=2 and not StringTools:-Search("$num","$RESPONSE")=0);

evalb(simplify((ANSWER)-($RESPONSE))=0);

Getting read of squareroots in the denominator try:
radnormal($q)
combine(simplify($q)) assuming a>0, b>0 if an and b are inside the squareroot
evala($q)
evala(Normal($q))

to enter Radicals use:
root(expr,root)  =  root(8,3)=2
surd(expr,root)  =  surd(8,3)=2

solve gives rational answers
fsolve gives decimal answers

Ratical/Fractional Exponents:
In your case you can set $ans to return the answer in its appropriate form, such as

$ans='2*sqrt(3)';

This would mean that sqrt(12) is graded incorrect, would that be okay? Are you are asking the student to convert to the simplest radical form?

Then use the Grading Code as follows:

ia := InertForm[Parse]("$ans");
ir := InertForm[Parse]("$RESPONSE");
is( value(ia) = value(ir) and op(0,ia) = op(0,ir) and map(value,{op(ia)}) = map(value,{op(ir)}) );



strcat


instringtool search only string is accepted if not use “” around.

$RESPONSE and $ANSWER are of type expression.

printf(``)  //put string contain inside no need to concatenate.

in eval “” convert expression into string.

put single quotes around the expression for $q which would prevent it from being evaluated e.g. $q = ‘($a*t)^$n';


Maple command
convert(expr, RootOf)

convert( expr, radical, n )


parse(string, option)   //convert string into expression, auto evaluation.


root(x,2)   ->   sqrt(x)


$ans=maple("if $opt1<$opt2 then $opt1 else $opt2 end if");
