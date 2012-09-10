# Copyright (C) 2012  Kouhei Sutou <kou@cozmixng.org>
#
# License: GPLv3+, GFDL and/or CC BY-SA 3.0
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

require "rabbit/task/slide"

spec = nil
Rabbit::Task::Slide.new do |task|
  spec = task.spec
end

desc "Tag #{spec.version}"
task :tag do
  sh("git", "tag", "-a", "-m", "#{spec.version} released!!!", spec.version.to_s)
end

desc "Release #{spec.version}"
task :release => [:publish, :tag] do
  sh("git", "push", "--tags")
end
