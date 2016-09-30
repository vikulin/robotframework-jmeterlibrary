Robot Framework JMeter Library

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as published by
the Free Software Foundation, either version 3 of the License, or
any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

Version 1.2 released on 30st of September 2016. Forked from http://sourceforge.net/p/rf-jmeter-py .

What's new:
    1.2 - Added JMeter 3.0 support

    Implementation of change request http://sourceforge.net/p/rf-jmeter-py/tickets/2/:
    " As a End User I want to have option to create smaller reports"

Following software versions were used during development:
- robotframework-2.8.7
- robotframework-ride-2.7.5
- JMeter 3.0
- python-2.7.5

Author: Vadym Vikulin

Website: https://github.com/vikulin/robotframework-jmeterlibrary

Installation:
- run command: pip install robotframework-jmeterlibrary

OR
- download, unzip and run command: python setup.py install

OR
- download, unzip and copy JMeterLib.py file to a directory pointed by
    PYTHONPATH (for example ...\Python27\lib\site-packages).

Example for running JMeter and parsing results in single keyword:
 | run jmeter analyse jtl convert | D:/apache-jmeter-2.12/bin/jmeter.bat | D:/Tests/Test1Thread1Loop.jmx | D:/Tests/output1.jtl |

Example for running JMeter and parsing results in separate keyword:
| ${logPath}= | set variable | D:/Tests/output1.jtl |  |
| run jmeter | D:/apache-jmeter-3.0/bin/jmeter.bat | D:/Tests/Test1Thread1Loop.jmx | ${logPath} |
| analyse jtl convert | ${logPath} |  |  |

Example for reading parsed contents:
| ${result} | analyse jtl convert | ${logPath} |  |
| log | ${result} |  |  |
| : FOR | ${ELEMENT} | IN |	@{result} |
|  | log dictionary	| ${ELEMENT} |  |