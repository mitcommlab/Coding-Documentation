# Code Styles: Reformatting Example

This block of text is hard to read and interpret, even though the variable names are very clear. Several lines  run off the page, so we’re definitely missing something interesting over there.

```matlab
for ii = 1:length(angleOfAttack)
liftCoefficient = zeros(size(relativeVelocity)); dragCoefficient = zeros(size(relativeVelocity));
for jj = 1:length(relativeVelocity)
wingSegments = contour2segments(wingPointCloud,numSegments,'Segment length','equal','Interpolation','linear');
[liftCoefficient(jj),dragCoefficient(jj)] = callXFOIL(wingSegments,angleOfAttack(ii),relativeVelocity(jj),'Options','default');
end
figure(ii);subplot(2,1,1);plot(relativeVelocity,liftCoefficient(ii,:),'b','LineWidth',2)
ylabel('Lift Coefficient C_L')
title(['2D Wing Performance at \alpha = ',num2str(angleOfAttack(ii)),' degrees'])
subplot(2,1,2);plot(relativeVelocity,dragCoefficient(ii,:),'r','LineWidth',2)
xlabel('Relative Velocity U [m/s]');ylabel('Drag Coefficient C_D')
end
```

---

Breaking at column 80, putting only one statement per line (notice ), and adding in some white space really helps readability. 

```matlab
for ii = 1:length(angleOfAttack)
liftCoefficient = zeros(size(relativeVelocity));
dragCoefficient = zeros(size(relativeVelocity));

for jj = 1:length(relativeVelocity)
wingSegments = contour2segments(wingPointCloud,numSegments,'SegmentLength',...
'equal','Interpolation','linear');

[liftCoefficient(jj),dragCoefficient(jj)] = callXFOIL(wingSegments,...
angleOfAttack(ii),relativeVelocity(jj),'Options','default');

end

figure(ii)
subplot(2,1,1)
plot(relativeVelocity,liftCoefficient(ii,:),'b','LineWidth',2)
ylabel('Lift Coefficient C_L')
title(['2D Wing Performance at \alpha = ',num2str(angleOfAttack(ii)),' degrees'])

subplot(2,1,2)
plot(relativeVelocity,dragCoefficient(ii,:),'r','LineWidth',2)
xlabel('Relative Velocity U [m/s]')
ylabel('Drag Coefficient C_D')

end
```

---

Add alignment structure by indenting once per logic level and once for continued lines (remember always with spaces; 4 for MATLAB). If you’re breaking lines of math at operators, place thee operator to the left of the new line, just like in a printed paper.

```matlab
for ii = 1:length(angleOfAttack)
	liftCoefficient = zeros(size(relativeVelocity));
	dragCoefficient = zeros(size(relativeVelocity));

	for jj = 1:length(relativeVelocity)
		wingSegments = contour2segments(wingPointCloud,numSegments,..
			'Segment length','equal','Interpolation','linear'); 

		[liftCoefficient(jj),dragCoefficient(jj)] = callXFOIL(wingSegments,...
			angleOfAttack(ii),relativeVelocity(jj),'Options','default');

	end

	figure(ii)
	subplot(2,1,1)
	plot(relativeVelocity,liftCoefficient(ii,:),'b','LineWidth',2)
	ylabel('Lift Coefficient C_L')
	title(['2D Wing Performance at \alpha = ',num2str(angleOfAttack(ii)),' degrees'])

	subplot(2,1,2)
	plot(relativeVelocity,dragCoefficient(ii,:),'r','LineWidth',2)
	xlabel('Relative Velocity U [m/s]')
	ylabel('Drag Coefficient C_D')

end
```

---

Get strategic with vertical alignment and grouping. The argument lists for two of the functions won’t fit on one line, so they’ve been grouped and aligned vertically. If adjacent arguments are related, they’re paired on the same row. 

```matlab
for ii = 1:length(angleOfAttack)
	liftCoefficient = zeros(size(relativeVelocity));
	dragCoefficient = zeros(size(relativeVelocity));

	for jj = 1:length(relativeVelocity)
		wingSegments = contour2segments(...
			wingPointCloud,numSegments,...
			'Segment length','equal',...
			'Interpolation','linear');

		[liftCoefficient(jj),dragCoefficient(jj)] = callXFOIL(...
			wingSegments,...
			angleOfAttack(ii),...
			relativeVelocity(jj),...
			'Options','default');

	end

	figure(ii)
	subplot(2,1,1)
	plot(relativeVelocity,liftCoefficient(ii,:),'b','LineWidth',2)
	ylabel('Lift Coefficient C_L')
	title(['2D Wing Performance at \alpha = ',num2str(angleOfAttack(ii)),' degrees'])
	
	subplot(2,1,2)
	plot(relativeVelocity,dragCoefficient(ii,:),'r','LineWidth',2)
	xlabel('Relative Velocity U [m/s]')
	ylabel('Drag Coefficient C_D')

end
```

---

If we rename some variables and functions, we can see how this alignment structure is invariant under refactoring.

```matlab
for ii = 1:length(angleOfAttack)
	liftCoefficient = zeros(size(relativeVelocity));
	dragCoefficient = zeros(size(relativeVelocity));

	for jj = 1:length(relativeVelocity)
		dirctedWingSegments = contour2planarsegments(...
			wingPointCloud,numSegments,...
			'Segment length','cosine spacing',...
			'Interpolation','cubic spline');

		[liftCoefficient(jj),dragCoefficient(jj)] = callXFOIL(...
			directedWingSegments,...
			angleOfAttack(ii),...
			relativeVelocity(jj),...
			'Options','ReynoldsNumber',1e6);

	end

	figure(ii)
	subplot(2,1,1)
	plot(relativeVelocity,liftCoefficient(ii,:),'b','LineWidth',2)
	ylabel('Lift Coefficient C_L')
	title(['2D Wing Performance at \alpha = ',num2str(angleOfAttack(ii)),' degrees'])
	
	subplot(2,1,2)
	plot(relativeVelocity,dragCoefficient(ii,:),'r','LineWidth',2)
	xlabel('Relative Velocity U [m/s]')
	ylabel('Drag Coefficient C_D')

end 
```

